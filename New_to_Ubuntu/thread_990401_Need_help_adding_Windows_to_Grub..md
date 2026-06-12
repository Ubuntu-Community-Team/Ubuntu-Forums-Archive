---
title: "Need help adding Windows to Grub."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by diablo75 on 2008-11-22
Someone I know just got their PC back from the techs at Best Buy and he gave them a spare hard drive to work with (because he didn't want them screwing his Ubuntu install up).  They installed a fresh instance of Windows on his PC.  He's made the Windows hard drive a slave and put his original Ubuntu hard drive back in as a master.  He'd like Grub to be able to see this Windows boot partition on the secondary drive so he can turn his PC into a dual-boot.  He's running Ubuntu 8.10.

---

### Post by jimmy the saint on 2008-11-22
Check out this thread:
[http://ubuntuforums.org/archive/index.php/t-237172.html](http://ubuntuforums.org/archive/index.php/t-237172.html)

---

### Post by hankinator on 2008-11-22
Hm.. I'm not to knowledgeable about grub, but if he understands the BIOS, why doesn't he just set it? cause the one time i messed around with grub, i lost all my data cause i couldn't recover. BIOS is much safer, well when just changing the boot order, slave and master don't matter, even tho i prefer cable select, its much more dynamic and error free, you just need to know your drive names.

---

### Post by handydan918 on 2008-11-22
this is a little complicated. The way to do this is to install the windows drive as master (because that is the gospel according to Bill) and install the Ubu drive as slave. Then reinstall grub. That should give you a fully functional dual-boot system.

---

### Post by shifty_powers on 2008-11-22
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

will still apply as it will restore grub with options for both

---

### Post by pastalavista on 2008-11-22
Download and burn a [Supergrub Disk]("http://www.supergrubdisk.org/"), boot from it and select the type system boot you want. It'll fix it automatically. Can't get any simpler.

---

### Post by caljohnsmith on 2008-11-22
Assuming your friend doesn't have any more drives than the Ubuntu master drive and Windows slave drive connected, just have him add the following entry in his Grub's menu.lst to boot Windows:
```
title	   Windows
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And to edit his menu.lst, he can use:
```
gksudo gedit /boot/grub/menu.lst
```
That should work, assuming Windows is on the 1st partition of the slave drive. If for some reason it doesn't work, then let me know exactly what happens when you try to boot Windows from the Grub menu, and also post:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

