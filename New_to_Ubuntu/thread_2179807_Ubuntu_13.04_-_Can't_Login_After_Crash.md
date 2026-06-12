---
title: "Ubuntu 13.04 - Can't Login After Crash"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by Richard_Bruce on 2013-10-10
Hi All,

My laptop, running Ubuntu 13.04 64-bit, just crashed while running `sudo /etc/init.d/networking restart`. I hit the power and made my way back to the log in screen, but after typing my password and hitting enter the screen went blank for a second and then came back to the log in screen. I can log in as a guest so it should be something related to my user settings.

It looks like crash when running `/etc/init.d/networking restart` is a known bug [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1102507](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1102507), but I cant find anyone who couldnt log into their account afterwards.

Please can someone help me get back into my user without reinstalling?


Cheers,
Richard

---

### Post by fantab on 2013-10-10
Delete .Xauthority file in your Home folder. You can reveal the hidden dot files by opening home and hitting Ctrl+H.

If you are having problem doing so then boot with Ubuntu DVD/USB... Open the Home folder on the hard disk and delete the said file. and restart with HDD.

---

### Post by Richard_Bruce on 2013-10-10
Frantastic, working again now.

Started in recovery mode and just renamed the file now everything is fine again.

Thanks alot!

---

