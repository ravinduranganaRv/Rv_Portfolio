# Ravindu Rangana: Portfolio

Static site (no build step). Files: `index.html`, `designs.json` (your portfolio items), `images/`.

## 1. Put it on GitHub (free hosting with GitHub Pages)
1. Sign in at github.com and click **New repository**. Name it `YOURUSERNAME.github.io` (site will be at `https://YOURUSERNAME.github.io`) or any name such as `portfolio` (site at `https://YOURUSERNAME.github.io/portfolio`). Set it to **Public**.
2. On the repo page click **uploading an existing file** and drag in everything from this folder (`index.html`, `designs.json`, `.nojekyll`, the whole `images` folder). Commit to the `main` branch.
3. Go to **Settings > Pages**. Under **Build and deployment** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then Save.
4. Wait 1 to 2 minutes. Your live link appears at the top of the Pages screen.

## 2. Make the admin panel publish for everyone
The admin panel saves new designs by committing them to your repo through the GitHub API, so you need a personal access token:
1. GitHub > your avatar > **Settings > Developer settings > Personal access tokens > Fine-grained tokens > Generate new token**.
2. Resource owner: you. **Only select repositories**: pick your portfolio repo. Permissions > Repository permissions > **Contents: Read and write**. Generate and copy the token.
3. Open your live site, click **Admin** in the footer (or add `#admin` to the address), and sign in.
4. In the dashboard, fill **GitHub connection** (owner, repo, branch `main`, token) and press **Save & test**.
5. Use **Add new design**. Each design is committed to the repo and appears on the site about a minute later.

The token is stored only in the browser you used. Do not share it. If it leaks, delete it in GitHub settings.

## Security notes
- The username/password screen runs in the browser, so it only keeps casual visitors out. What actually protects your site is that nobody can change it without your GitHub token.
- To change the password, run this in your browser console and replace the 64-character value after `const H=` near the top of the admin section of `index.html`:
  `crypto.subtle.digest("SHA-256",new TextEncoder().encode("USERNAME|NEWPASSWORD")).then(b=>console.log([...new Uint8Array(b)].map(x=>x.toString(16).padStart(2,"0")).join("")))`

## Other free hosts
Cloudflare Pages and Netlify also work: connect the same repo, no build command, publish directory `/`.
