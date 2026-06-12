---
title: "Upgraded now hangs after login"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by reven1320 on 2008-07-18
I recently upgraded to the newest ubuntu software. It allows me to get to the login page but afterwards the background changes to a blank blue screen and simply hangs there. When I tried to load in safemode, I noticed an error message:

*Setting kernel variables...
error: "vm.mmap_min_addr" is an unknown key.

I don't know if this is even related to the first problem. Any help please. I'm pretty new to Ubuntu.

By the way the upgrade was completed by the download manager.

---

### Post by markjensen on 2008-07-18
When it does that, have you actually tried to login?  Or is it happening at the gdm user login screen before you get the chance to login?

Also, verify that you can login via text TTY terminal by pressing CTRL+ALT+F2 to get a TTY login, then attempt to enter your username and password at the prompts.    This will help see if it is an X/video issue, or a whole system issue.

---

### Post by reven1320 on 2008-07-18
Ok, I have tried logging in at the login prompt and under TTY, both accept my username and password. But as I said previously, when I login at the orginal ubuntu login page, the next screen I get is a blank page. It never progresses from that screen. Any additional advice?

---

### Post by markjensen on 2008-07-18
Ok, your first post never said you were able to log in.  Just that you got to the screen.  Then the background changed to blank blue after.

It looks like your gnome configuration (for whatever reason) is bad.   I'm not a Gnome guy, but you should be able to rename your 'dot' file (like .gnome) to something else so it won't be used when Gnome starts (yet is still available to you to recover your settings).

A little less potentially destructive would be to do something like **sudo apt-get install fluxbox** at your command prompt when you are logged into a TTY terminal.  Then restart your computer (or just get back to the login screen), and select a Session of "fluxbox" from the login screen.  This should allow you to log into a GUI session of fluxbox.   If it is just a Gnome issue, this will be fine.  If it is a larger issue with X or gdm login manager, then this will also not work.

---

### Post by reven1320 on 2008-07-18
> **markjensen said:**
> Ok, your first post never said you were able to log in.  Just that you got to the screen.  Then the background changed to blank blue after.

It looks like your gnome configuration (for whatever reason) is bad.   I'm not a Gnome guy, but you should be able to rename your 'dot' file (like .gnome) to something else so it won't be used when Gnome starts (yet is still available to you to recover your settings).

A little less potentially destructive would be to do something like **sudo apt-get install fluxbox** at your command prompt when you are logged into a TTY terminal.  Then restart your computer (or just get back to the login screen), and select a Session of "fluxbox" from the login screen.  This should allow you to log into a GUI session of fluxbox.   If it is just a Gnome issue, this will be fine.  If it is a larger issue with X or gdm login manager, then this will also not work.

Sorry about the misunderstanding there. I tried logging into a GUI session of fluxbox but it didn't work. 
I rec'd a message saying to run apt-get update. Tried that but then was told to run the same command again with the message that index files failed to download.

---

### Post by markjensen on 2008-07-18
If **sudo apt-get update** is failing, then you may have larger problems than I am familiar with. :(

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

