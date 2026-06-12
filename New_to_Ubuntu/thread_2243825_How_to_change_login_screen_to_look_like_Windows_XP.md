---
title: "How to change login screen to look like Windows XP?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Jose_Torres on 2014-09-11
Hello!

I am migrating my old Netbook from Windows XP to Lubuntu (14.04).

Already installed successfully Lubuntu.  No dual boot.  Clean installed.

I found threads to make the desktop looked like Windows XP but non how to make the Login screen looked like Windows XP.

Specifically, I need to see the list of users as Distinct Icons not as Drop Down list.  
So to click the Icon and then enter password if any or non for auto logon users, the same way as Windows XP does.

The Netbook will be used by small children that already knows how to login in Windows XP (without password), just by mouse clicks, so I want to keep it simple.

Any help will be appreciated.

---

### Post by pissedoffdude on 2014-09-16
Mint's display manager provides this kind of functionality.  To install and use it: 
```
sudo add-apt-repository ppa:noobslab/mint
sudo apt-get update
sudo apt-get install mdm mdm-themes
```

Then reboot and look for a program called "Login Window Preferences" (I'm not entirely sure of its location, but it should be somewhere in the settings submenu).  Choose the appropriate theme and logout.

---

