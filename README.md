# MERN Blog Capstone Project

This is a full-stack MERN (MongoDB, Express, React, Node.js) blog application featuring Role-Based Access Control (RBAC), image uploads with Cloudinary, and robust authentication using JWT. 

## Features

- **Role-Based Access Control (RBAC):** Three distinct roles:
  - **USER:** Can read articles, view profiles, and add comments.
  - **AUTHOR:** Can write, edit, delete, and manage their own articles, as well as read and comment.
  - **ADMIN:** Can manage users, authors, and oversee the platform.
- **Authentication:** Secure login and registration utilizing JSON Web Tokens (JWT) stored in HTTP-only cookies, with password hashing via bcryptjs.
- **Profile Image Uploads:** Integrates with Multer and Cloudinary to securely upload and serve user profile pictures.
- **Article Management:** Create, view, update, and soft-delete articles.
- **Responsive UI:** Built with React, Tailwind CSS, and Vite for a modern and responsive user experience.
- **State Management:** Uses Zustand for lightweight and fast global state management.

## Tech Stack

### Frontend
- **Framework:** React 19 with Vite
- **Styling:** Tailwind CSS 4
- **Routing:** React Router 7
- **State Management:** Zustand
- **Form Handling:** React Hook Form
- **API Calls:** Axios

### Backend
- **Environment:** Node.js
- **Framework:** Express.js 5
- **Database:** MongoDB with Mongoose
- **Authentication:** JWT, cookie-parser, bcryptjs
- **File Uploads:** Multer, Cloudinary API

## Prerequisites

Before you begin, ensure you have the following installed on your machine:
- Node.js (v18+)
- MongoDB (running locally or a MongoDB Atlas URI)
- Cloudinary Account (for image uploads)

## Installation & Setup

1. **Clone the repository or navigate to the project directory:**
   ```bash
   cd NEW
   ```

2. **Backend Setup:**
   Navigate to the backend directory and install dependencies:
   ```bash
   cd backend
   npm install
   ```

3. **Backend Environment Variables:**
   In the `backend` folder, create a `.env` file (if not present) and add the following keys:
   ```env
   PORT=5000
   DB_URL=<Your MongoDB URI>
   SECRET_KEY=<Your JWT Secret Key>
   CLOUDINARY_CLOUD_NAME=<Your Cloudinary Cloud Name>
   CLOUDINARY_API_KEY=<Your Cloudinary API Key>
   CLOUDINARY_API_SECRET=<Your Cloudinary API Secret>
   ```

4. **Frontend Setup:**
   Open a new terminal, navigate to the frontend directory, and install dependencies:
   ```bash
   cd frontend
   npm install
   ```

## Running the Application

1. **Start the Backend Server:**
   In the `backend` directory, run:
   ```bash
   npm start
   # or node server.js
   ```
   The backend should start running on `http://localhost:5000`.

2. **Start the Frontend Development Server:**
   In the `frontend` directory, run:
   ```bash
   npm run dev
   ```
   The frontend should start running (usually on `http://localhost:5173` or similar based on Vite).

## Project Structure

```
NEW/
│
├── backend/
│   ├── apis/            # Express route handlers (userapi, authorapi, adminapi, commonapi)
│   ├── config/          # Configuration files (Cloudinary, Multer)
│   ├── middleware/      # Custom middlewares (verifytoken)
│   ├── models/          # Mongoose schemas (usermodel, articlemodel)
│   ├── server.js        # Entry point for the Node.js server
│   ├── package.json
│   └── .env             # Environment variables
│
└── frontend/
    ├── src/
    │   ├── components/  # Reusable React components (Home, Register, UserProfile, etc.)
    │   ├── store/       # Zustand store (authStore)
    │   ├── styles/      # Shared styling configuration
    │   ├── App.jsx      # Main App component with Routing
    │   └── main.jsx     # Vite entry point
    ├── package.json
    └── tailwind.config.js
```

## API Routes Overview

- `/common-api/register`: User and Author registration (handles image upload).
- `/common-api/login`: Authenticates the user and sets an HTTP-only JWT cookie.
- `/common-api/logout`: Clears the JWT cookie.
- `/common-api/check-auth`: Verifies active session on page reloads.
- `/user-api/articles`: Fetches all active articles.
- `/user-api/article/:articleId`: Fetches a specific article.
- `/user-api/comment`: Adds a comment to an article.
- `/author-api/article`: Creates a new article (AUTHOR only).
- `/author-api/article/:articleId`: Updates/Deletes an article (AUTHOR only).

## License

This project is licensed under the ISC License.
