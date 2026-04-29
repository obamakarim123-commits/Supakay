# Supakay Company - Deployment Guide

## Prerequisites for Vercel Deployment

### 1. Set up MongoDB Atlas
- Create a MongoDB Atlas cluster at https://www.mongodb.com/cloud/atlas
- Create a database user with credentials
- Get your connection string

### 2. Environment Variables

For Vercel, add this environment variable in your project settings:

```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/database?retryWrites=true&w=majority
```

Locally, create a `.env.local` file (copy from `.env.example`) and fill in your MongoDB URI.

### 3. Deploy to Vercel

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Add environment variable through CLI or dashboard
```

## Project Structure

- `/app` - Next.js app directory with pages and API routes
- `/app/api` - Backend API endpoints
- `/app/api/health` - MongoDB connection health check endpoint

## Testing

Before deploying:

```bash
npm run build  # Verify build succeeds
npm run dev    # Test locally with MONGODB_URI in .env.local
```

Visit `http://localhost:3000/api/health` to verify MongoDB connection works.

## Notes

- ⚠️ Never commit `.env.local` - it contains secrets
- Vercel will use environment variables from project settings
- MongoDB connection strings must be whitelisted for Vercel's IP addresses
