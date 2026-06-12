---
title: "Out of space in boot partition"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by Arnett_Carroll on 2015-05-15
I have Ubuntu Linux 14.04 LTS installed on my Dell D510 laptop.  I am receiving an error message saying that my /boot partition is full.  What do I need to do? I was denied access to the files in the partition.

---

### Post by v3.xx on 2015-05-15
I like this one

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Other ways here

[URL="http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu"]http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu

[COLOR=#ff0000]Edit[/COLOR]
Your running a boot partition?
[/URL]

---

### Post by ajgreeny on 2015-05-15
Yes, why have you got a separate /boot partition as it more often than not ends up causing this exact problem?

If you have chosen encryption or to use LVM a separate /boot partition will be necessary and made by the system automatically at installation. It is then essential that you manage kernel that are installed manually and keep only the current version plus the previous version to avoid this problem.

Otherwise it is not worth the hassle of a separate /boot partition.

Try terminal command **sudo apt-get autoremove** which may work, but may also not be able to carry out the operation due to lack of free space, in which case come back again for more help.

---

