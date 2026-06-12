---
title: "Updated linux and xbmc, now xbmc won't load"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by ccdavis77 on 2014-07-17
Hello-
After performing standard recommended linux upgrades (and xbmc upgrade), now xbmc won't load, just keeps flashing briefly then crashes back to login screen. Help please!

Crash log:
pastebin.com/QvzXEQ0f

---

### Post by sp40140 on 2014-07-18
Could you add bit more details:
Hardware specs (specially vid card). 
Do you have xbmc autostart?
when you say "just keeps flashing briefly then crashes back to login screen", does that mean that you are getting logged out of Ubuntu? as there is no log-in for xbmc that I know of.
Also, which version of xbmc do you currently have. What was your previous version of xbmc?

---

### Post by ccdavis77 on 2014-07-18
Sure,thanks. No separate video card, intel i3 processor. My HTPC runs ubuntu but usually boots directly into xbmc which was working fine for months until I upgraded recommended updates and xbmc last night. Now it tries 3 times to load xbmc which flashes briefly on the screen then ultimately crashes and goes to login dialog box where you can choose to log into either ubuntu or xbmc.  Running XBMC (14.0-ALPHA1 Git:a891415). Platform: Linux x86 64-bit, Running on Ubuntu 14.04 LTS, kernel: Linux x86 64-bit version 3.13.0-32-generic

---

### Post by Bucky Ball on 2014-07-18
Could you open a terminal in Ubuntu and run the updates again. 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please report any errors that show up.

* Just reread your post. You can't boot into Ubuntu? When you are at the login screen after the crash, can't you select the Unity session from the 'Session' drop-down menu? If you could get to a desktop would help your cause.

---

### Post by ccdavis77 on 2014-07-18
I can get to the desktop. Dialog box is "select desktop environment" can choose as default either ubuntu or xbmc. I usually set it to xbmc to have it boot directly into the application.

---

### Post by sp40140 on 2014-07-18
What happens if you try to manually launch xbmc from desktop? Also, do you have Unity desktop or have you installed any other environments like lxde?

---

### Post by ccdavis77 on 2014-07-18
Just ubuntu desktop. Won't load from desktop either, crashes on startup

heres a debug log from xbmc if that's helpful...

Pastebin.com/9aLEXaKJ

---

### Post by sp40140 on 2014-07-18
CCDavis
From the logs.. it looks like you are running ALPHA build of XBMC version 14.0. Is this correct? if so, Why are you running alpha build?
Alpha builds are usually not stable. The current stable released version is 13.1 Gotham.
Please move back to stable version of XBMC.

first line from log:
Starting XBMC (14.0-ALPHA1 Git:a891415). Platform: Linux x86 64-bit

Cheers,

---

### Post by ccdavis77 on 2014-07-18
It just updated through ubuntu desktop. I tried via terminal to point to stable release. How can I go back to stable? Would be glad to.

---

### Post by sp40140 on 2014-07-18
Try section 6.1 from XBMC FAQ:
[http://wiki.xbmc.org/index.php?title=XBMC_v13_%28Gotham%29_FAQ](http://wiki.xbmc.org/index.php?title=XBMC_v13_%28Gotham%29_FAQ)

---

### Post by ccdavis77 on 2014-07-18
I just scrapped it and started over. Kept my user folder and xbmc at least runs now...however my addons are gone and they won't download. Good times.

---

### Post by Bucky Ball on 2014-07-18
Not a great result, but at least the original problem is gone. Either way, please mark thread as solved to help others and post a new thread about anything else if you need to. Good luck. ;)

---

### Post by ccdavis77 on 2014-07-19
Thanks, will do.

---

