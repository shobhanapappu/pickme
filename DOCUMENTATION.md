# PickMe Intelligence Platform Documentation

## Overview

PickMe Intelligence is a comprehensive law enforcement OSINT (Open Source Intelligence) platform designed specifically for police departments and law enforcement agencies. The platform provides secure, scalable intelligence gathering capabilities with both free OSINT searches and premium API-based verification services.

## Table of Contents

1. [System Architecture](#system-architecture)
2. [Features Overview](#features-overview)
3. [User Roles & Access](#user-roles--access)
4. [Frontend Components](#frontend-components)
5. [Backend Services](#backend-services)
6. [Database Schema](#database-schema)
7. [API Integration](#api-integration)
8. [Security Features](#security-features)
9. [Deployment Guide](#deployment-guide)
10. [Usage Instructions](#usage-instructions)

## System Architecture

### Technology Stack

**Frontend:**
- React 18 with TypeScript
- Tailwind CSS for styling
- React Router for navigation
- Lucide React for icons
- React Hot Toast for notifications
- Recharts for data visualization
- Date-fns for date handling

**Backend:**
- Node.js with Express
- Supabase for database and authentication
- Python scripts for OSINT scraping
- JWT for authentication
- Winston for logging
- Redis for caching
- Rate limiting and security middleware

**Database:**
- PostgreSQL (via Supabase)
- Row Level Security (RLS)
- Comprehensive audit logging
- Automated migrations

**External Integrations:**
- Signzy API for phone verification
- Surepass API for identity verification
- Telegram Bot API
- WhatsApp Business API (planned)

## Features Overview

### Core Capabilities

1. **OSINT Intelligence Gathering**
   - Free social media searches
   - Email and username lookups
   - Public records search
   - Cross-platform profile discovery

2. **Premium Verification Services**
   - Phone number verification (Signzy)
   - Identity document verification (Surepass)
   - Credit history checks
   - Vehicle registration verification
   - Cell tower location services

3. **Multi-Platform Access**
   - Web portal (admin and officer)
   - Telegram bot integration
   - WhatsApp bot (planned)
   - REST API access

4. **Administrative Features**
   - Officer management
   - Credit system management
   - API key management
   - Real-time monitoring
   - Comprehensive reporting
   - Audit trail maintenance

## User Roles & Access

### Admin Users
- **Full System Access**: Complete control over all platform features
- **Officer Management**: Create, update, suspend, and delete officer accounts
- **Credit Management**: Allocate, top-up, and track credit usage
- **API Management**: Configure and monitor external API integrations
- **System Monitoring**: Real-time dashboard and performance metrics
- **Audit Access**: Complete audit trail and compliance reporting

### Officers
- **Query Access**: Perform OSINT and PRO searches
- **Credit Tracking**: Monitor personal credit balance and usage
- **History Access**: View personal query history
- **Profile Management**: Update personal information and preferences
- **Multi-Platform Access**: Web portal, Telegram, and WhatsApp

## Frontend Components

### Admin Portal (`/admin/*`)

#### Dashboard (`/admin/dashboard`)
- Real-time system statistics
- Officer activity monitoring
- Query success rates
- Credit usage analytics
- Recent activity feeds

#### Officer Management (`/admin/officers`)
- Officer profile management
- Status control (Active/Suspended)
- Credit allocation
- Performance statistics
- Bulk operations

#### Registration Management (`/admin/registrations`)
- Review pending officer registrations
- Approve/reject applications
- Automated account creation
- Notification system

#### Query History (`/admin/queries`)
- Complete query audit trail
- Advanced filtering and search
- Export capabilities
- Performance analytics

#### Credit Management (`/admin/credits`)
- Credit transaction history
- Bulk credit operations
- Revenue tracking
- Payment processing

#### API Management (`/admin/apis`)
- External API configuration
- Usage monitoring
- Cost tracking
- Health checks

#### Live Monitoring (`/admin/live`)
- Real-time request tracking
- System performance metrics
- Active officer monitoring
- Alert management

#### System Settings (`/admin/settings`)
- Platform configuration
- Security settings
- Notification preferences
- User management

### Officer Portal (`/officer/*`)

#### Officer Login (`/officer/login`)
- Secure authentication
- Registration request system
- Multi-factor authentication support

#### Officer Dashboard (`/officer/dashboard`)
- Personal statistics
- Quick action buttons
- Recent activity
- Credit balance

#### Query Interfaces
- **Free Lookups**: Mobile check, email verification, platform scanning
- **PRO Lookups**: Phone prefill, RC verification, credit history, cell ID
- **TrackLink**: URL tracking and analytics
- **History**: Personal query history and results

### Landing Page (`/`)
- Public-facing information
- Feature overview
- Access portals
- Contact information

## Backend Services

### Express Server (`server/index.js`)
- RESTful API endpoints
- Authentication middleware
- Rate limiting
- CORS configuration
- Error handling
- Request logging

### Route Handlers

#### Authentication (`/api/auth`)
- User login/logout
- Token verification
- Password management
- Session handling

#### Officer Management (`/api/officers`)
- CRUD operations
- Status management
- Statistics retrieval
- Bulk operations

#### Query Processing (`/api/queries`)
- Query execution
- Result storage
- History retrieval
- Export functionality

#### Credit System (`/api/credits`)
- Transaction processing
- Balance management
- Usage tracking
- Reporting

#### API Management (`/api/apis`)
- External API configuration
- Usage monitoring
- Health checks
- Cost tracking

#### Live Monitoring (`/api/live`)
- Real-time data
- Performance metrics
- Active sessions
- System health

#### Dashboard Analytics (`/api/dashboard`)
- Statistical summaries
- Performance metrics
- Activity feeds
- System status

### Python Services

#### OSINT Scraper (`server/osint/scraper.py`)
- Social media searches
- Email verification
- Username lookups
- Public records search
- Cross-platform correlation

#### Telegram Bot (`server/bot/telegram.py`)
- Natural language processing
- Command handling
- Authentication
- Rate limiting
- Result formatting

#### External API Integrations
- **Signzy API** (`server/pro-apis/signzy.py`): Phone verification services
- **Surepass API** (`server/pro-apis/surepass.py`): Identity verification services

## Database Schema

### Core Tables

#### `admin_users`
- System administrators and moderators
- Authentication credentials
- Role-based permissions
- Activity tracking

#### `officers`
- Law enforcement personnel
- Contact information
- Credit balances
- Status management
- Performance metrics

#### `officer_registration_requests`
- Pending officer applications
- Approval workflow
- Rejection tracking
- Automated processing

#### `requests`
- Query execution records
- Input/output tracking
- Performance metrics
- Status monitoring

#### `request_logs`
- Raw JSON result storage
- File attachments
- Metadata tracking
- Audit compliance

#### `credit_transactions`
- Credit allocation/deduction
- Payment processing
- Transaction history
- Audit trail

#### `api_usage`
- External API call tracking
- Cost monitoring
- Performance metrics
- Error logging

#### `api_keys`
- External service credentials
- Usage limits
- Cost tracking
- Security management

#### `audit_logs`
- System activity tracking
- User actions
- Security events
- Compliance reporting

#### `system_settings`
- Platform configuration
- Feature flags
- Operational parameters
- Environment settings

### Security Features

#### Row Level Security (RLS)
- Table-level access control
- User-based data isolation
- Role-based permissions
- Audit compliance

#### Data Encryption
- API key encryption
- Sensitive data protection
- Secure transmission
- At-rest encryption

#### Authentication & Authorization
- JWT token management
- Multi-factor authentication
- Session management
- Role-based access control

## API Integration

### External Services

#### Signzy API
- **Purpose**: Phone number verification and owner details
- **Cost**: 2-3 credits per query
- **Features**: 
  - Owner name resolution
  - Carrier information
  - Location data
  - Confidence scoring

#### Surepass API
- **Purpose**: Identity document verification
- **Cost**: 2-3 credits per query
- **Features**:
  - Aadhaar verification
  - PAN verification
  - Driving license validation
  - Voter ID verification

### Internal APIs

#### Query Processing API
```
POST /api/queries/process
- Executes OSINT or PRO queries
- Handles credit deduction
- Stores results and logs
- Returns formatted responses
```

#### Officer Management API
```
GET /api/officers
POST /api/officers
PUT /api/officers/:id
DELETE /api/officers/:id
PATCH /api/officers/:id/status
```

#### Credit Management API
```
GET /api/credits/transactions
POST /api/credits/add
POST /api/credits/deduct
GET /api/credits/stats
```

## Security Features

### Authentication
- JWT-based authentication
- Secure password hashing (bcrypt)
- Session timeout management
- Multi-factor authentication support

### Authorization
- Role-based access control
- Resource-level permissions
- API endpoint protection
- Database-level security

### Data Protection
- API key encryption
- Sensitive data masking
- Secure transmission (HTTPS)
- Audit trail maintenance

### Rate Limiting
- Per-user query limits
- API endpoint throttling
- Abuse prevention
- Fair usage policies

### Compliance
- Complete audit logging
- Data retention policies
- Privacy protection
- Regulatory compliance

## Deployment Guide

### Prerequisites
- Node.js 18+
- Python 3.9+
- Supabase account
- External API credentials

### Environment Setup

#### Frontend Environment (`.env`)
```
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

#### Backend Environment
```
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
JWT_SECRET=your_jwt_secret_key
API_ENCRYPTION_KEY=your_encryption_key
PORT=3001
NODE_ENV=production
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
SIGNZY_API_KEY=your_signzy_api_key
SUREPASS_API_KEY=your_surepass_api_key
```

### Database Setup
1. Create Supabase project
2. Run migrations in order:
   - `20250703151456_violet_lodge.sql`
   - `20250705030206_round_limit.sql`
   - `20250705033807_solitary_star.sql`
3. Seed initial data using `server/database/seed.js`

### Application Deployment
1. Install dependencies: `npm install`
2. Build frontend: `npm run build`
3. Start backend: `npm run server`
4. Configure reverse proxy (nginx/Apache)
5. Set up SSL certificates
6. Configure monitoring and logging

### Bot Deployment
1. Install Python dependencies: `pip install -r server/bot/requirements.txt`
2. Configure bot credentials
3. Deploy to cloud service (AWS/GCP/Azure)
4. Set up monitoring and health checks

## Usage Instructions

### Admin Portal Usage

#### Initial Setup
1. Access admin portal at `/admin/login`
2. Use default credentials: `admin@pickme.intel` / `admin123`
3. Configure system settings
4. Add API keys for external services
5. Create initial officer accounts

#### Officer Management
1. Navigate to Officers section
2. Add new officers manually or approve registrations
3. Allocate credits and set permissions
4. Monitor officer activity and performance

#### System Monitoring
1. Use Dashboard for real-time overview
2. Monitor Live Requests for active queries
3. Review Query History for audit purposes
4. Track credit usage and revenue

### Officer Portal Usage

#### Getting Started
1. Register at `/officer/login`
2. Wait for admin approval
3. Receive login credentials
4. Access dashboard at `/officer/dashboard`

#### Performing Queries
1. **Free OSINT Searches**:
   - Mobile Check: Basic phone number information
   - Email Check: Social media and breach data
   - Platform Scan: Username searches across platforms

2. **Premium PRO Searches**:
   - Phone Prefill: Detailed owner information
   - RC Verification: Vehicle registration details
   - Credit History: Financial background checks
   - Cell ID: Location services

#### Managing Credits
1. Monitor balance in dashboard
2. Request top-ups through admin
3. Track usage history
4. Optimize query efficiency

### Telegram Bot Usage

#### Setup
1. Contact @PickMeIntelBot on Telegram
2. Use `/register` command with credentials
3. Wait for admin approval
4. Start querying with `/osint` or `/pro`

#### Commands
- `/start` - Welcome and help
- `/register` - Officer registration
- `/osint <query>` - Free OSINT search
- `/pro <query>` - Premium search (requires credits)
- `/status` - Account information
- `/credits` - Credit balance
- `/history` - Recent queries
- `/help` - Detailed help

#### Natural Language Queries
- "Find owner of 9791103607"
- "Search social media for john.doe@email.com"
- "Verify AADHAAR 123456789012"

## Support and Maintenance

### Monitoring
- System health dashboards
- Performance metrics
- Error tracking
- Usage analytics

### Backup and Recovery
- Automated database backups
- Configuration backups
- Disaster recovery procedures
- Data retention policies

### Updates and Maintenance
- Regular security updates
- Feature enhancements
- Performance optimizations
- Bug fixes and patches

### Support Channels
- Technical documentation
- Admin training materials
- User guides
- Support ticket system

---

## Conclusion

PickMe Intelligence provides a comprehensive, secure, and scalable platform for law enforcement intelligence gathering. With its multi-platform access, robust security features, and extensive audit capabilities, it meets the demanding requirements of modern police operations while maintaining compliance with regulatory standards.

For technical support or feature requests, please contact the development team or refer to the detailed API documentation and user guides.