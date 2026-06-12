---
title: "can't access ubuntu 13.10 install"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by dyrien66 on 2014-01-10
I lost power and my computer running ubuntu 13.10 crashed, when I rebooted I got grub "error: no such partition".
I have samba server configured, virtual machines installed, and multiple user accounts.
When I boot to live cd I can see this all on my hard drive but cannot boot into it.

I tried to reinstall ubuntu and keep settings and data, when I rebooted I got same error.
I then purged and reinstalled grub (using chroot from live cd), after this I am able to boot from my hard drive but it is into a new install and my mouse(ps2) doesn't work.(My mouse worked fine before and works fine when booted in live cd.

Is there anyway to get access back to my original install? (When I boot to live cd I can see all my accounts and vm's on my hard drive).
If not is there anyway I can back up my accounts, vm's, and settings, reinstall then restore?
 I will attach file from boot info script.

---

### Post by carl4926 on 2014-01-10
If the data is there / visible from the live session
You could use something like Parted Magic to boot a live session and copy the stuff you need. Parted Magic should have no problem with permissions
I have a older copy of it here: [https://dl.dropboxusercontent.com/u/10573557/pmagic-4.5.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic-4.5.iso)

However, your comments beg some questions:
You said you re-installed? Presumably you didn't format your installation partition?
Did you use exactly the same username as previously?

---

### Post by dyrien66 on 2014-01-10
The data is backed up, what I really want to save is all the configuration I have already done. I reinstalled with the option to keep my settings. No I did not format. I used the same account name for root and password but the computer name is different. I am missing the user accounts and my mouse doesn't work which makes it very hard to get anything done so I am running off a live cd instead.

---

### Post by carl4926 on 2014-01-11
The essential part is set here
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/xubuntu_13.10/11.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/xubuntu_13.10/11.png)
The username has to match exactly 

The computer name should be the same as before unless you previously altered it (you can do) but this identifies it on the network

All your settings are mostly in hidden folders in your username

---

### Post by carl4926 on 2014-01-11
If you are talking about things like samba or ssh, those things are part of the root system and will have been overwritten

---

### Post by dyrien66 on 2014-01-11
The usernames do match exactly.
So basically even though I picked the install option to keep user settings it overwrote them anyway...and I have lost use of my mouse as well.

---

### Post by dyrien66 on 2014-01-11
Thank you for your help I will reinstall and hope it works better this time.

---

