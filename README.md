# E-Commerce MVP Implementation Blueprint

This repository now includes the implemented product blueprint for an Ikman.lk-style marketplace MVP, organized for execution across product, engineering, security, QA, and launch.

## 1) Scope Definition

### User Roles
- **Buyer**: browse/search listings, save items, chat with sellers, place orders, track status.
- **Seller**: create/manage listings, respond to chats, manage orders, receive payouts.
- **Admin/Moderator**: review reports, moderate listings/users, handle disputes, monitor trust and abuse.

### Core User Flows
1. Sign up/login (phone OTP or email verification).
2. Seller posts listing with images, category, price, location.
3. Buyer discovers listing through search, category, filter, and sort.
4. Buyer contacts seller via in-app chat.
5. Buyer completes checkout/payment (MVP can start with COD + one online gateway).
6. Seller confirms fulfillment; buyer tracks and confirms completion.
7. Buyer can report fraud/spam; admin reviews and takes action.

### MVP Feature List
- Authentication + profile management
- Listing CRUD with media upload
- Search/filter/sort
- Real-time chat
- Notifications (push + in-app)
- Basic checkout/payment flow
- Reporting + moderation

## 2) Product Modules

- **Account/Profile**: onboarding, auth, profile details, identity state.
- **Listings**: create/edit/delete listings, inventory state, image gallery.
- **Discovery**: category browsing, text search, faceted filtering, sorting.
- **Chat**: buyer-seller threads, message delivery/read states.
- **Notifications**: order, chat, moderation, and account alerts.
- **Orders/Payments**: cart/intent, payment status, fulfillment lifecycle.

## 3) Architecture

### Client Structure (Android-aligned domain model)
- Presentation layer: screens + view models per module.
- Domain layer: use-cases for auth/listings/search/chat/order/report.
- Data layer: repository pattern (remote + local cache).

### Backend/API Approach
- REST/JSON APIs for core entities: users, listings, chats, orders, reports.
- Event hooks for notifications and moderation workflows.
- Versioned endpoints with role-based authorization.

### Database Model (Core Entities)
- `users`, `profiles`, `roles`
- `listings`, `listing_images`, `categories`
- `chats`, `chat_messages`
- `orders`, `payments`, `payouts`
- `reports`, `moderation_actions`
- `notifications`, `device_tokens`

### Cloud/Storage Setup
- Object storage for listing images.
- Managed relational DB for transactional entities.
- Push notification service for Android devices.
- Centralized logging + monitoring pipeline.

## 4) Security and Trust

- Auth with short-lived access tokens + refresh strategy.
- OTP/email verification during onboarding.
- Role-based access control and endpoint authorization.
- Input validation/sanitization on all write APIs.
- Anti-spam controls: rate limits, listing throttles, suspicious activity flags.
- User reporting, moderation queues, and enforceable account/listing actions.

## 5) UI/UX and Localization

### Navigation Map
- Home → Search Results → Listing Detail → Chat/Checkout
- Seller Dashboard → Listing Management → Order Management
- Profile → Settings → Language/Notifications
- Admin Console → Reports Queue → Moderation Action

### Key Screens
- Auth, onboarding, home feed, search/filter, listing detail, compose listing, chat, checkout, order tracking, profile/settings, admin moderation.

### Localization
- Support **Sinhala / Tamil / English** from MVP.
- Externalized strings, language toggle in settings.
- Locale-aware currency/date formatting.

## 6) MVP Phase Delivery

1. **Phase A**: Authentication + profiles  
2. **Phase B**: Listings module  
3. **Phase C**: Search/filter/sort  
4. **Phase D**: Chat and messaging reliability  
5. **Phase E**: Checkout/payment and order lifecycle

## 7) Operations Layer

- Product analytics for funnel and retention metrics.
- Crash and error monitoring with alerting.
- Admin support tooling for disputes and abuse handling.
- Defined customer support workflow and response SLAs.

## 8) Validation Strategy

- Unit tests for domain/business logic.
- UI tests for critical user paths.
- API contract and integration tests.
- Device compatibility matrix and release candidate checks.
- Closed beta feedback loop with prioritized issue triage.

## 9) Launch Readiness

- Play Store assets and release metadata.
- Privacy policy + terms of use published.
- Production runbook + incident response contacts.
- Go-live checklist (security, performance, analytics, support).
- Post-launch iteration plan based on telemetry + user feedback.

---

## Local Development

Prerequisites:
- Node.js 18+ and npm

```sh
# From /home/runner/work/Stock-Management/Stock-Management
npm install
npm run dev
```

The app runs on the Vite local URL shown in terminal (typically `http://localhost:5173`).
