---
title: "[SOLVED] No desktop/termanal/anything after update"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Samanathon on 2008-07-08
Hi all, I'm relatively new to Linux and I'm sure that I'll be using the wrong names for things, but here I go:

I installed Ubuntu 8.04 this morning and everything went smooth, the system prompted me to update (228 updates) and I did, then I was told to restart. Now, after I enter in my user name and password, all I can see is my desktop picture - no menus, mouse or anything else!

I tried ALT+F2, but nothing happens. The only commands that seem to work are CTRL+F(1-7) but I don't know any commands to enter into these terminals!

Please help! I really want to use Ubuntu....

---

### Post by Inxsible on 2008-07-08
Restart the computer and this time select "recovery mode"

See if you can get in there. It will just show you a prompt (No GUI)...but atleast we can fix things from there.

---

### Post by Samanathon on 2008-07-08
I was able to get into recovery mode and I tried "Repair broken packages" and "Try to fix x server" without success.

I did try:
```
sudo apt-get --reinstall install ubuntu-desktop
```

and that fixed it, apparently, I uninstalled something that I shouldn't have...

**THANKS FOR THE HELP!!!**

---

### Post by Inxsible on 2008-07-08
> **Samanathon said:**
> I was able to get into recovery mode and I tried "Repair broken packages" and "Try to fix x server" without success.

I did try:
```
sudo apt-get --reinstall install ubuntu-desktop
```and that fixed it, apparently, I uninstalled something that I shouldn't have...

**THANKS FOR THE HELP!!!**
Glad you got it working. :)

---

