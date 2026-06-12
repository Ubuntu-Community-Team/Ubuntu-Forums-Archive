---
title: "Ubuntu Budgie on OracleVM - &quot;Desktop&quot; is not loading properly"
date: 2017-08-11
forum: New to Ubuntu
---

### Post by kranton on 2017-08-11
Hi guys, i am a newbie. I am planning to switch to Linux in a long run, but for now i am playing around with Distros.

Just installed ubuntu budgie 17.04 on me OracleVM 5.1.12 with Extentions, after installing Guest Additions and restarting, i've got this:

[IMG]https://i.imgur.com/RbBcddW.png[/IMG]
[I]
**What went wrong?**[/I] Where is my default dock?(that "thingie" on the left side) And the context menu(right click) only has those 2 options.

Addition#1
I have found my "Dock" it's called Plank. I started it, and it looked "weird". After restart - it's not on desktop anymore. I assume, some scripts do not execute properly, but i have no clue which ones and where to look for them.

Addition#2
Thanks for the help. When i tried to remove libreoffice-calc
 ```
sudo apt-get remove libreoffice-calc
```
...
The following packages will be REMOVED:
  *budgie-desktop-environment* libreoffice-calc [I]ubuntu-budgie-desktop


[/I]I did not expect that...

---

### Post by davidmohammed on 2017-08-11
very odd - looks like some key packages have somehow been uninstalled.

    sudo apt install --reinstall ubuntu-budgie-desktop budgie-desktop-environment

then reboot

---

### Post by kranton on 2017-08-11
Thank you ! That seems to have fixed the issue.
Also i know what happened. Will update my first post.

---

