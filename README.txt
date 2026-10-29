URBANKING VALORANT ONLINE OVERLAY — SETUP

Files in this folder:
- overlay.html: OBS browser overlay, keeps your original visual design
- control.html: sign-in protected online control panel
- config.js: project URL and publishable key configuration
- urbanking-logo.png: overlay logo

IMPORTANT: The Supabase publishable key is designed for browser use. Never add a Supabase secret key or service_role key to this folder or GitHub.

BEFORE PUBLISHING
1. Open config.js in a text editor.
2. Replace PASTE_YOUR_SUPABASE_PUBLISHABLE_KEY_HERE with your key beginning sb_publishable_. Keep the surrounding single quotes.
3. Save the file.
4. Upload overlay.html, control.html, config.js, and urbanking-logo.png to the root of your GitHub repository.
5. In GitHub, open Settings > Pages. Under Build and deployment, choose Deploy from a branch, select main and /(root), then Save. Wait for deployment.
6. Your overlay URL will be https://urbankingplays.github.io/urbanking-valorant-overlay/overlay.html
7. Your control panel URL will be https://urbankingplays.github.io/urbanking-valorant-overlay/control.html
8. In OBS, add a Browser Source with the overlay URL. Set width 810 and height 190.
9. Open control.html in your browser, sign in with the user you created in Supabase Authentication, then edit values and click UPDATE OVERLAY. OBS polls for updates every 2 seconds.

SECURITY / TROUBLESHOOTING
- The table should have RLS enabled. Public reads are intentional for the overlay. Updates are restricted by your policy to the authenticated email configured in Supabase.
- If sign-in fails, verify the email/password in Supabase Authentication > Users and check Supabase Authentication URL Configuration if needed.
- If saving fails, check the policy on public.overlay_state. The policy should allow UPDATE only when auth.jwt()->>'email' matches your account email.
- Never commit database passwords, secret API keys, or service_role keys.
- Keep your original local ZIP as a backup.
