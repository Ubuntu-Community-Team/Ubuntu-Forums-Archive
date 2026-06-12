---
title: "Error while installing in Windows 7"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by munko93 on 2013-04-14
Please help me, this is the error I get when trying to install ubuntu 12.10 on windows 7 64 bit. [IMG]http://i.imgur.com/Jr8aDzl.png[/IMG]

---

### Post by oldos2er on 2013-04-14
Post moved to its own thread.

---

### Post by gerowen on 2013-04-14
If you want to try it out without actually repartitioning your drive, I recommend just using a virtual machine with software like Oracle's Virtualbox ([www.virtualbox.org](www.virtualbox.org)).  I've always had issues with Wubi.

---

### Post by oldfred on 2013-04-14
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

   HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

