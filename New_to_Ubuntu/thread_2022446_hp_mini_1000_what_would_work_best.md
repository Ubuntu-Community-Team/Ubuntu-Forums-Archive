---
title: "hp mini 1000 what would work best"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by koll on 2012-07-11
whats the best linux distro for an hp mini 1000 it has intel atom 1.6 dual core 1 gig memory and 16 gigs of storage and broad com wireless i love ubuntu 12.4 i use it on my other two computers bit i believe its too bulky i have tried hp mi but theit is noting but a few games so if any one knows what i should try please let me know thanks

---

### Post by mastablasta on 2012-07-11
if you like Ubuntu you could try with Unity 2D. that should free up some system resources.
otherwise.... Xubuntu Lubuntu
you can also try KDE with netbook interface (netbook plasma or something...).

---

### Post by Gone fishing on 2012-07-11
I think you have enough power to run Ubuntu 12.04 fine. However, you could run Xubuntu or even something lighter like Fluxbox. I would do it by installing Ubuntu 12.04 and then the other window managers xubuntu-desktop fluxbox etc. When you login you can choose your windows manager and decide which you like best.

---

### Post by NikTh on 2012-07-11
Ubuntu 12.04 LTS **32bit** , on ubuntu-2d mode. You will be fine i think. After installation completes and at login screen click the gear-like symbol and choose ubuntu-2d.

---

### Post by black veils on 2012-07-11
Ubuntu in 2D mode or Xubuntu (it has plenty of options). if you find that even with Xubuntu it is slow (which i would be surprised at), you can change the swappiness value. swappiness is default 60, which is only needed for servers, for normal desktop use, you only need about 10. here's how:

open the Terminal and copy-paste:
```
gksudo gedit /etc/sysctl.conf
```press Enter key

Scroll to the bottom of the text file and add your swappiness parameter to override the default, so copy/paste the following lines:
```
#
# Decrease swap usage to a workable level
vm.swappiness=10

```Close the text file and reboot your computer.

After the reboot, check the new swappiness value:
open the Terminal and copy-paste:
```
cat /proc/sys/vm/swappiness
```press Enter key

Now it should be the chosen new value.

---

### Post by koll on 2012-07-11
thanks im downloading xbuntu now ill post how it works out

---

### Post by Ubun2to on 2012-07-11
> **koll said:**
> thanks im downloading xbuntu now ill post how it works out

Make sure it is the ***_32 BIT_*** version, as NikTh said. Also, if you think it takes up to much space, check this out:
[https://help.ubuntu.com/community/Installation/MinimalCD/](https://help.ubuntu.com/community/Installation/MinimalCD/)
Just 27 MB for the Ubuntu 12.04 LTS 32 Bit ISO.

---

### Post by koll on 2012-07-11
so im lovin xbuntu it was hard to get the broad com wireless drivers woking but so far im happy with it

---

