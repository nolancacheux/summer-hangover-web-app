# Summer Hangover - Group Event Planning Platform

A comprehensive web application designed to streamline group event planning, expense management, and social coordination. Developed in 2023/2024.

## Table of Contents

- [Overview](#overview)
- [Team](#team)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

Summer Hangover is a modern web application that simplifies the process of organizing social events, managing group expenses, and coordinating activities. Built with scalability and user experience in mind, it provides an intuitive platform for groups to plan, vote on, and participate in various events while maintaining transparent expense tracking.

## Team

- Nathan Eudeline
- Cyprien Kelma
- Nolan Cacheux
- Paul Pousset
- Julien De Almeida

## Key Features

### Group Management
- Create and manage groups with customizable settings
- Role-based access control (administrators and members)
- Invitation system via QR codes and shareable links
- Member management and permissions

### Event Planning
- Collaborative event creation and scheduling
- Activity proposals and democratic voting system
- Real-time participation tracking
- Flexible date and time management

### Expense Tracking
- Integrated expense management system
- Automatic cost splitting and balance calculation
- Transparent transaction history
- Simplified reimbursement workflows

### Communication
- Built-in real-time chat system
- Event-specific discussion threads
- Push notifications for important updates
- Activity feed and announcements

### Analytics & Insights
- Hall of Fame featuring member statistics
- Event participation metrics
- Spending patterns and insights
- Group activity dashboards

## Technology Stack

### Frontend
- **Framework:** Next.js 14 with TypeScript
- **UI Library:** React 18
- **Styling:** TailwindCSS + Material-UI
- **State Management:** React Context API

### Backend
- **Database:** LibSQL with Turso (Edge Database)
- **ORM:** Drizzle ORM
- **API Layer:** tRPC for type-safe APIs
- **Authentication:** NextAuth.js

### Infrastructure & Services
- **Hosting:** Vercel Edge Network
- **Real-time:** Pusher WebSockets
- **File Storage:** UploadThing
- **Maps Integration:** Google Maps API
- **Monitoring:** Built-in analytics

## Architecture

### System Design

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│   Next.js App   │────▶│   tRPC API     │────▶│   Turso DB     │
│                 │     │                 │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
        │                       │                       │
        │                       │                       │
        ▼                       ▼                       ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│     Pusher      │     │  Google Maps   │     │  UploadThing   │
│                 │     │                 │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

### Data Model

The application uses a relational data model with the following core entities:

- **Users:** Profile information, preferences, authentication data
- **Groups:** Group metadata, member relationships, settings
- **Events:** Event details, schedules, locations
- **Activities:** Activity proposals, votes, descriptions
- **Expenses:** Transactions, balances, payment records
- **Messages:** Chat messages, notifications, system alerts

## Installation

### Prerequisites

- Node.js 18+ and npm/yarn/pnpm
- Git
- Database URL (Turso)
- API keys for external services

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/Bafbi/summer-hangover.git
   cd summer-hangover
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env.local
   ```
   
   Update `.env.local` with your credentials:
   ```env
   DATABASE_URL=your_turso_database_url
   DATABASE_AUTH_TOKEN=your_turso_auth_token
   NEXTAUTH_SECRET=your_nextauth_secret
   NEXTAUTH_URL=http://localhost:3000
   PUSHER_APP_ID=your_pusher_app_id
   PUSHER_KEY=your_pusher_key
   PUSHER_SECRET=your_pusher_secret
   PUSHER_CLUSTER=your_pusher_cluster
   NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_key
   UPLOADTHING_SECRET=your_uploadthing_secret
   UPLOADTHING_APP_ID=your_uploadthing_app_id
   ```

4. **Set up the database**
   ```bash
   npm run db:push
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```

6. **Access the application**
   ```
   http://localhost:3000
   ```

### Production Deployment

The application is optimized for deployment on Vercel:

1. Fork the repository
2. Connect to Vercel
3. Configure environment variables
4. Deploy

## Usage

### For End Users

1. **Account Creation**
   - Register with email
   - Complete profile setup
   - Verify account

2. **Group Creation**
   - Click "Create Group"
   - Configure group settings
   - Invite members via link or QR code

3. **Event Planning**
   - Select group
   - Create new event
   - Add activities
   - Set date and location

4. **Expense Management**
   - Add expenses during events
   - Review balance
   - Settle payments

### For Developers

1. **Database Management**
   ```bash
   npm run db:studio  # Open Drizzle Studio
   npm run db:push    # Push schema changes
   npm run db:pull    # Pull schema from database
   ```

2. **Development Commands**
   ```bash
   npm run dev        # Start development server
   npm run build      # Build for production
   npm run start      # Start production server
   npm run lint       # Run ESLint
   npm run type-check # Run TypeScript compiler
   ```

3. **Testing**
   ```bash
   npm run test       # Run test suite
   npm run test:watch # Run tests in watch mode
   ```

## API Documentation

### Authentication Endpoints

- `POST /api/auth/signin` - User authentication
- `POST /api/auth/signout` - User logout
- `GET /api/auth/session` - Get current session

### tRPC Procedures

The application uses tRPC for type-safe API calls. Key procedures include:

- `group.create` - Create new group
- `group.join` - Join existing group
- `event.create` - Create new event
- `event.vote` - Vote on activities
- `expense.add` - Add new expense
- `expense.settle` - Settle payments

## Contributing

We welcome contributions to Summer Hangover! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit your changes**
   ```bash
   git commit -m "Add your feature"
   ```
4. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request**

### Development Guidelines

- Follow TypeScript best practices
- Maintain existing code style
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed

### Code Style

- Use ESLint configuration
- Follow existing patterns
- Keep components small and focused
- Use TypeScript strict mode

## Deployment Costs

### Estimated Monthly Costs (10,000 users)

| Service | Cost | Description |
|---------|------|-------------|
| Pusher | $500 | Real-time messaging (Premium plan) |
| Google Maps API | $1,650 | Location services (~4 requests/user/month) |
| Vercel | $100 | Hosting and deployment |
| Turso | $417 | Database hosting |
| **Total** | **$2,667** | Monthly operational cost |

### Monetization Strategy

- **Premium Features:** Advanced planning tools, unlimited groups, priority support
- **Business Partnerships:** Featured venues and activities
- **Sponsored Events:** Collaborative event promotion
- **Analytics Services:** Anonymized trend data for market research

## Performance & Scalability

### Current Capacity
- Supports 100 concurrent users (free tier)
- Sub-second response times
- 99.9% uptime SLA

### Scaling Strategy
- Horizontal scaling via Vercel Edge Network
- Database replication with Turso
- CDN for static assets
- Caching layer for frequently accessed data

## Security

- End-to-end encryption for sensitive data
- OAuth 2.0 authentication
- Rate limiting and DDoS protection
- Regular security audits
- GDPR compliant data handling

## Roadmap

### Upcoming Features
- Mobile application (React Native)
- Advanced analytics dashboard
- AI-powered activity recommendations
- Multi-language support
- Calendar integrations
- Payment gateway integration

---

**Repository:** [https://github.com/Bafbi/summer-hangover](https://github.com/Bafbi/summer-hangover)  
**Live Demo:** [https://eventsync.app](https://eventsync.app)  
**Documentation:** [https://docs.eventsync.app](https://docs.eventsync.app)