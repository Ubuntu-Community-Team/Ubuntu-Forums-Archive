---
title: "macbook wireless guide out of date"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by flavio newbie on 2008-06-13
in the wireless guide [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) we are asked to download stuff, the madwifi, but the links are both broken!!

---

### Post by Joeb454 on 2008-06-13
If you already know how to do this, you can edit that wiki page. Either way I'll pass it on to a wiki team :)

---

### Post by LaRoza on 2008-06-13
This forum doesn't have any control over the ubuntu pages or wiki. When you find errors or isssues with them, inform those sites, not this one.

---

### Post by Rocket2DMn on 2008-06-13
You can add requests like that to the WikiToDo page or email the doc-team mailing list 
WikiToDo - [https://help.ubuntu.com/community/WikiToDo](https://help.ubuntu.com/community/WikiToDo)
mailing list - [https://lists.ubuntu.com/mailman/listinfo/ubuntu-doc](https://lists.ubuntu.com/mailman/listinfo/ubuntu-doc)

---

### Post by flavio newbie on 2008-06-13
ok, but anyone can tell me what to do for the problem?

---

### Post by Rocket2DMn on 2008-06-13
I don't know anything about using MadWifi since I don't have an Apple, but you can have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)
It seems that that madwifi website is down, but the drivers should already be in the linux-restricted-modules package for your kernel, and you can download the package madwifi-tools
```
sudo apt-get install linux-restricted-modules-`uname -r` madwifi-tools
```
From there, I honestly don't know.  If that link doesn't help you solve your problem, consider making a post in the Networking and Wireless forum area - [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Good luck!

---

