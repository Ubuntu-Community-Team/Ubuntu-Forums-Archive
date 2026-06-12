---
title: "Password after boot.."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by KS1987 on 2008-10-05
Can I enable an option that asks for a password after Ubuntu is loaded? So that I choose auto login, but that I have to enter a password when I want to use my loaded Ubuntu. Thank in advance!

---

### Post by bobnutfield on 2008-10-05
Why would you want to have an automatic login AND require a password to use the system?  The login window serves the same purpose for each user.

---

### Post by jamesrl on 2008-10-05
I wouldn't suggest this for security, since this is less secure than the original method (where you type your password before being logged in). 

However, if you run the screensaver that is set to lock screen as part of the start up sequence you could.
E.g., go to Preferences->Sessions-> Add startup programs and have one be
```
gnome-screensaver-command --activate
```
and be sure gnome-screensaver is configured to lock the screen.

---

### Post by handydan918 on 2008-10-05
> **KS1987 said:**
> Can I enable an option that asks for a password after Ubuntu is loaded? So that I choose auto login, but that I have to enter a password when I want to use my loaded Ubuntu. Thank in advance!

I can't see either how or why you would do this. The whole purpose of auto-login is to bypass the password requirement. 
Now, you could probably set it up to lock the  screensaver and require a password to unlock it, but that wouldn't be exactly the same.
What is it you are trying to accomplish?
:confused:

Never mind. I see I was beaten on the draw by jamesrl...

---

### Post by KS1987 on 2008-10-05
Good idea, thank you. I would use this, so I can start my computer up, come back later and don't have to wait for something to load, but make it secure, so nobody can take advantage of it..

---

