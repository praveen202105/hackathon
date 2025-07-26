# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **Project Kisan** - an AI-powered farming solutions platform built with Next.js 15 and integrated with Python-based agentic AI systems. The platform provides crop diagnosis, multilingual farmer assistance, and agricultural intelligence services targeting Indian farmers.

## Development Commands

### Next.js Frontend
```bash
npm run dev          # Start development server at http://localhost:3000
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
```

### Python Backend (Agricultural Agent)
```bash
cd root-python/Agentic1/multi_tool_agent/
pip install -r requirements.txt
python advanced_agricultural_agent.py
```

## Architecture

### Frontend Structure (Next.js App Router)
- **`app/`** - App Router pages and API routes
  - **`api/`** - API endpoints for diagnosis, satellite data, multimodal analysis
  - **Page components** - `diagnosis/`, `farmer-assistant/`, `login/`, etc.
- **`components/`** - React components with shadcn/ui design system
  - **`MultimodalFarmerChat.tsx`** - Main chat interface for farmer assistance
  - **`ui/`** - shadcn/ui component library
- **`src/`** - Core application logic
  - **`lib/`** - Authentication (NextAuth.js), MongoDB connection, utilities
  - **`models/`** - MongoDB/Mongoose data models (User, Farm, Crop, Task)

### Backend Structure (Python Agentic System)
- **`root-python/Agentic1/multi_tool_agent/`** - Main AI agent directory
  - **`advanced_agricultural_agent.py`** - Core multimodal AI agent
  - **`agent.py`** - Base agent implementation
  - **FastAPI integration** for web services
  - **Google Cloud Vertex AI** integration for AI processing

### Key Technologies

**Frontend Stack:**
- Next.js 15 with App Router
- TypeScript
- Tailwind CSS + shadcn/ui components
- NextAuth.js for authentication
- MongoDB/Mongoose for data persistence

**Backend Stack:**
- Python with FastAPI
- Google Cloud Vertex AI (Gemini models)
- Google Generative AI SDK
- Agentic framework for autonomous AI behavior

**AI Capabilities:**
- Multimodal analysis (text + image processing)
- Multilingual support (English, Kannada, Hindi)
- Crop disease detection and diagnosis
- Agricultural advisory services
- Real-time satellite data integration

## Authentication & Database

- **NextAuth.js** configured with credentials provider
- **MongoDB** for user data, farm records, and task management
- User roles: farmer, admin, consultant
- JWT tokens for API authentication

## Key Features

1. **Leaf Disease Diagnosis** - Upload plant images for AI-powered disease detection
2. **Multilingual Farmer Chat** - Voice and text support in regional languages
3. **Market Intelligence** - Real-time crop pricing and market data
4. **Satellite Data Integration** - Agricultural monitoring via satellite imagery
5. **Government Schemes** - Information about agricultural subsidies and programs

## API Endpoints

- **`/api/diagnose`** - Plant disease diagnosis from uploaded images
- **`/api/multimodal-analysis`** - Comprehensive agricultural analysis
- **`/api/satellite-data`** - Satellite imagery and agricultural monitoring
- **`/api/auth/[...nextauth]`** - NextAuth.js authentication

## Environment Variables

Required for full functionality:
- `JWT_SECRET` - JWT token signing secret
- `MONGODB_URI` - MongoDB connection string
- `NEXTAUTH_SECRET` - NextAuth.js secret
- `FIREBASE_SERVICE_ACCOUNT_KEY` - Firebase Admin SDK service account (JSON string)
- Google Cloud credentials for Vertex AI integration

## Firebase Configuration

**Firebase Project**: `farmeruserdb`
- **Authentication**: Email/Password enabled
- **Firestore**: User profiles stored in `users` collection
- **Client Config**: Located in `src/lib/firebase.ts`
- **Admin Config**: Located in `src/lib/firebaseAdmin.ts`

### Firebase Setup Steps:
1. Enable Authentication with Email/Password in Firebase Console
2. Create Firestore database
3. Download service account key and set `FIREBASE_SERVICE_ACCOUNT_KEY` env var
4. Users are stored in both Firestore (Firebase) and MongoDB (legacy)

## Testing & Quality

- TypeScript for type safety
- ESLint for code quality
- Development includes both jest and pytest for cross-platform testing
- Image processing with OpenCV and Pillow

## Deployment Notes

- Next.js application deployable on Vercel
- Python backend requires Google Cloud Platform setup
- MongoDB Atlas recommended for production database
- Requires Google Cloud Vertex AI API access for AI features