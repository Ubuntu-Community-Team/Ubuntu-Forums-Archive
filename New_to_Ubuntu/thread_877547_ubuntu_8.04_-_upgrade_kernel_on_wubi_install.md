---
title: "ubuntu 8.04 - upgrade kernel on wubi install"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by J2897 on 2008-08-01
I have Installed Ubuntu for the first time (successfuly) to try out [aircrack-ng]("http://www.aircrack-ng.org/doku.php?id="). For 'injection' to work, my kernel version must be at least 2.6.25. My current kernal version is 2.6.24.

This is what I need to install...
[http://aircrack-ng.org/doku.php?id=iwl3945&DokuWiki=799b2d357dad2045ebcc47e03b4608a2](http://aircrack-ng.org/doku.php?id=iwl3945&DokuWiki=799b2d357dad2045ebcc47e03b4608a2)

**Please be aware that this is my first time using Linux!**

For days I have been trying to figure out how to upgrade the kernel to 2.6.25 on a wubi install (I installed Ubuntu by mounting the Ubuntu .ISO from within Vista on the same machine; currently set up to tripple boot Ubuntu, Vista & XP). I have been unsuccessful in upgrading the kernel. I downloaded a Patch from here...
[http://kernel.org/](http://kernel.org/)
"The latest stable version of the Linux kernel is:     2.6.26    2008-07-13 22:44 UTC"
... I couldn't figure out what I was supposed to do with it; I couldn't find instructions or tutorials for my specific task/requirements. So I eventually tried...
```
update-manager -d
```
... I noticed that it stated, "New Distribution Release '8.10' is available". It was an '8.10 Alpha 3' version (Intrepid Ibex) with a kernel version of 2.6.27. Though after update/install, it failed to Restart my system properly (Black Screen of Discomfort (lol!)). I manually switched off then on and selected Ubuntu from the Boot Menu. I crashed on the Ubuntu loading screen. Luckily I had previously backed-up the Ubuntu disk image. I restored the image.

I've also posted here in some more detail relating to aircrack-ng...
[http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=e8fc0ae8227128dc267e8c096ac92678&topic=3917.msg22320#msg22320](http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=e8fc0ae8227128dc267e8c096ac92678&topic=3917.msg22320#msg22320)

---

