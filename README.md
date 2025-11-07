# Intellector Analyzer - GitHub Pages Host

This directory contains the built static files for deployment to GitHub Pages.

## Setup Instructions

**IMPORTANT: Enable GitHub Pages BEFORE pushing the workflow!**

1. **Push this directory to a GitHub repository** named `intellector-analyzer-host` (or update the base path in `frontend/vite.config.js` to match your repository name)

2. **Enable GitHub Pages FIRST** (Required before workflow can run):
   - Go to your repository Settings → Pages
   - Under "Build and deployment":
     - Source: **GitHub Actions**
   - Save (this creates the Pages environment)

3. **Push your code** - GitHub Actions will automatically deploy when you push to the main branch

**Note:** If you see "Get Pages site failed" error, it means GitHub Pages isn't enabled yet. Enable it manually in Settings → Pages first, then re-run the workflow.

## Manual Deployment

If you prefer manual deployment:

1. Build the frontend:
   ```bash
   cd ../frontend
   npm run build
   ```

2. Copy the dist folder contents to this directory:
   ```bash
   Copy-Item -Path "frontend\dist\*" -Destination "intellector-analyzer-host\" -Recurse -Force
   ```

3. Commit and push:
   ```bash
   git add .
   git commit -m "Deploy to GitHub Pages"
   git push
   ```

## Important Notes

- The `.nojekyll` file ensures GitHub Pages serves all files correctly
- The base path is configured as `/intellector-analyzer-host/` in the Vite config
- If your repository name is different, update `frontend/vite.config.js` base path before rebuilding

## Repository Structure

```
intellector-analyzer-host/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions workflow
├── assets/                     # Built assets (JS, CSS)
├── index.html                  # Main HTML file
└── .nojekyll                   # Disable Jekyll processing
```

