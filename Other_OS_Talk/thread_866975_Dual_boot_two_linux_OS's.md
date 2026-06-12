---
title: "Dual boot two linux OS's"
date: 2008-07-22
forum: Other OS Talk
---

### Post by Lecotti on 2008-07-22
Hi all, i am intending to dual boot Debian 4.0 and ubuntu 8.04, i already have ubuntu installed. Now i know that GRUB is very good at detecting windows partitions but i have heard that it is not so hot at detecting other linux ones(i am intending to share one swap partition) so i have 2 questions. 
1) Does the debian installer automaticly install grub or does it have to be installed manualy(also on the installer) 

2) will Grub detect both ubuntu and debian and allow me to boot into both, help would be appreciated!

---

### Post by aomlives on 2008-07-22
I have a triple boot Ubuntu 8.04 - OpenSUSE - Windows XP. I installed first Windows, then OpenSUSE and then Ubuntu and I had no notable problems with grub. You just have to make sure Debian installs grub too during installation, and you should be fine. :)

---

### Post by Lecotti on 2008-07-22
Thanks!!

---

### Post by SunnyRabbiera on 2008-07-22
well ubuntu's bootloader is a little more notorious of bypassing other linuxes, but dual booting another linux should work

---

### Post by kk0sse54 on 2008-07-22
Check out this thread [http://ubuntuforums.org/showthread.php?t=724817&highlight=multi+boot](http://ubuntuforums.org/showthread.php?t=724817&highlight=multi+boot) ,it's a great howto written by bodhi.zazen.

---

### Post by ibutho on 2008-07-22
One thing you can do is install Ubuntu first and let it install grub to the MBR. After that install Debian and let it install grub to the root partition you created for Debian. After that edit grub in Ubuntu and let it chainload the Debian grub e.g. in Ubuntu add something like.

```

title Debian
	root (hd1,1)
	makeactive
        chainloader +1

```
Change root (hd1,1) to the device name of your Debian partition.

---

### Post by rsambuca on 2008-07-22
> **ibutho said:**
> One thing you can do is install Ubuntu first and let it install grub to the MBR. After that install Debian and let it install grub to the root partition you created for Debian. After that edit grub in Ubuntu and let it chainload the Debian grub e.g. in Ubuntu add something like.

```

title Debian
	root (hd1,1)
	makeactive
        chainloader +1

```
Change root (hd1,1) to the device name of your Debian partition.
I very much prefer this method as well since you don't have to worry about manually updating grub with kernel changes.  You just edit it the first time and you are done.

---

