---
title: "Clean install of 22.04.1 and accounts are not asking for password after first login"
date: 2023-01-20
forum: New to Ubuntu
---

### Post by habadashler on 2023-01-20
Hi, I did a clean install of 22.04.1 minimal and joined the server to the domain.  All accounts that login, including the local account created during install ask for the password at login.  Every subsequent login only requires the username.  While I'm sure that is cached locally on each client, my bigger concern is that this server is accessible via shared console and I'm able to login with other users just using their username.  In my searching, the solutions seem to be editing either lightdm or gdm3, which, if I'm understanding correctly, are parts of the user interface we don't want or need installed.  

Is there a way to force requiring a password at every login using only the command line minimal install?

Thanks for your time and help!

---

### Post by TheFu on 2023-01-20
IDK anything about AD and don't have 22.04.
The screen on desktops with the login is created either by lightdm or gdm3.  That's kinda important.
I've never bypassed entering login credentials, so I wouldn't know how to accomplish that.

---

