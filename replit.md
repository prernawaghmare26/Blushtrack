# BlushTrack - AI-Powered Menstrual Health Tracker

## Overview

BlushTrack is a comprehensive menstrual health tracking application that combines traditional cycle logging with AI-powered insights to help users understand their bodies and health patterns. The application features a React frontend with TypeScript, an Express.js backend, and PostgreSQL database with Drizzle ORM for data management.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **UI Components**: shadcn/ui component library with Radix UI primitives
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod validation
- **Charts**: Recharts for data visualization
- **Build Tool**: Vite for development and building

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Runtime**: Node.js with ES modules
- **Session Management**: Simple in-memory session storage (currentUser variable)
- **API Design**: RESTful endpoints with JSON responses
- **Validation**: Zod schemas shared between frontend and backend

### Data Storage Solutions
- **Database**: PostgreSQL (configured for Neon Database)
- **ORM**: Drizzle ORM with TypeScript support
- **Migration Strategy**: Drizzle Kit for schema migrations
- **Development Storage**: In-memory storage implementation for development
- **Connection**: @neondatabase/serverless for database connectivity

### Key Database Tables
- **users**: User accounts with preferences and cycle settings
- **period_logs**: Menstrual period tracking with flow intensity
- **daily_logs**: Daily mood, symptoms, and notes
- **ai_insights**: AI-generated health insights and recommendations
- **goals**: User-defined health and tracking goals
- **notifications**: System notifications and reminders

## Key Components

### Authentication System
- Email/password authentication with basic session management
- User registration with email verification capability
- Password reset functionality (structure in place)
- Simple session middleware for protected routes

### Cycle Tracking Features
- **Period Logging**: Start/end dates with flow intensity tracking
- **Daily Logs**: Mood slider (1-5 scale), symptom checkboxes, notes
- **Calendar View**: Color-coded cycle visualization with predictions
- **Analytics**: Charts showing cycle patterns, mood trends, symptom correlations

### AI Integration
- **OpenAI Integration**: GPT-4o model for generating health insights
- **Insight Types**: Daily, weekly, monthly, and cycle-based recommendations
- **AI Chat**: Interactive health assistant for questions
- **Confidence Scoring**: AI provides confidence levels for insights

### User Interface
- **Responsive Design**: Mobile-first approach with desktop optimization
- **Dark/Light Theme**: Theme provider with system preference detection
- **Navigation**: Header with role-based navigation and mobile drawer
- **Component Library**: Comprehensive UI components with consistent styling

## Data Flow

### User Registration/Login Flow
1. User submits credentials via frontend form
2. Backend validates with Zod schemas
3. User data stored in database/memory storage
4. Session established with simple user ID tracking
5. Frontend redirects to onboarding or dashboard

### Period Tracking Workflow
1. User logs period data through dashboard or dedicated log page
2. Data validated and stored in period_logs table
3. Calendar component updates with new period information
4. Analytics recalculate cycle patterns and predictions

### AI Insight Generation
1. User triggers insight generation or automatic daily generation
2. Backend collects user's cycle data, symptoms, and patterns
3. OpenAI API processes data and generates personalized insights
4. Insights stored with confidence scores and recommendations
5. Frontend displays insights with appropriate UI components

### Dashboard Data Aggregation
1. Dashboard queries multiple endpoints for comprehensive view
2. Combines period logs, daily logs, AI insights, and predictions
3. Real-time cycle phase calculation based on last period and average length
4. Quick logging interface for immediate data entry

## External Dependencies

### Core Framework Dependencies
- **React Ecosystem**: React, React DOM, React Hook Form, TanStack Query
- **UI Libraries**: Radix UI primitives, shadcn/ui components, Lucide icons
- **Styling**: Tailwind CSS, class-variance-authority for component variants
- **Date Handling**: date-fns for date manipulation and formatting
- **Charts**: Recharts for data visualization

### Backend Dependencies
- **Server Framework**: Express.js with TypeScript support
- **Database**: Drizzle ORM, Neon Database serverless driver
- **AI Integration**: OpenAI SDK for GPT-4o integration
- **Development**: tsx for TypeScript execution, esbuild for production builds

### Development Tools
- **Build Tools**: Vite with React plugin and runtime error overlay
- **Type Checking**: TypeScript with strict mode enabled
- **Database Tools**: Drizzle Kit for migrations and schema management
- **Linting/Formatting**: Configured for TypeScript and React best practices

## Deployment Strategy

### Build Process
- **Frontend**: Vite builds optimized React application to `dist/public`
- **Backend**: esbuild bundles Express server to `dist/index.js`
- **Database**: Drizzle migrations applied via `db:push` command
- **Environment**: Production builds use NODE_ENV=production

### Environment Configuration
- **Database**: PostgreSQL connection via DATABASE_URL environment variable
- **AI Services**: OpenAI API key configuration for GPT-4o access
- **Development**: Local development with tsx and Vite dev server
- **Production**: Single Node.js process serving both API and static files

### Hosting Considerations
- **Database**: Configured for Neon Database (PostgreSQL-compatible)
- **Static Assets**: Express serves built React application in production
- **API Routes**: All backend routes prefixed with `/api`
- **Development**: Vite dev server with HMR and backend proxy setup

### Security Features
- **Data Privacy**: No data selling policy, HIPAA compliance considerations
- **Session Security**: Basic session management (expandable to secure tokens)
- **Input Validation**: Comprehensive Zod schemas for all user inputs
- **Error Handling**: Proper error responses and logging throughout application