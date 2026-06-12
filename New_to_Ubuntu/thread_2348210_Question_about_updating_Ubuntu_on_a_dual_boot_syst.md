---
title: "Question about updating Ubuntu on a dual boot system."
date: 2017-01-01
forum: New to Ubuntu
---

### Post by fighuass on 2017-01-01
I have a PC with both Windows 10 and Ubuntu 16.04 on it, and I want to update to Ubuntu 16.10. There's a catch, though. I want to remove Ubuntu 16.04 and all of the data completely (because there's a lot of garbage and clutter on it) without affecting Windows 10. After that, I want to install Ubuntu 16.10 and start from scratch again. How do I approach this?

---

### Post by oldfred on 2017-01-01
You still have to make sure Windows fast start up is off.
But some older versions, did not see Windows correctly (when fast start was on) and erased system.

So best to always have full backup before any major system changes. You should be doing regular backups anyway, just make sure it is current. And backup means on some other device. Users have picked wrong options and erased entire drive.

Safest is to use something Else. I normally partition in advance and often have an old install like 15.04 that I want to install 17.04 into.
I just choose Something Else, select partition with old install (change button) and install to that partition. It will auto find existing swap.
If you want to change partitions around, better to do that with gparted before installing.

Screen shots.
 UEFI install  Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
SSD & HDD, but I prefer full backup before deleting recovery partitions
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.

---

### Post by RobGoss on 2017-01-01
You should be able to use the same partition that Ubuntu 16.04 is install on, it will use that partition in the same manner as the first installation. You do realize 16.04 has longer support then 16.10 right!

If you created that partition using Windows you can also do it that way using Disk management, it will allow you to delete that partition and reclaim that space or you can just delete the Ubuntu partition and use the allocated space for your new installation of 16.10 

Ether way it's not to complicated seeing you want to do a fresh installation 

As fred stated make sure you have your windows backed up 

Best of luck

---

### Post by gordintoronto on 2017-01-02
It seems like you don't want an update, you want a fresh install. You might as well do a fresh install of 16.04, since it has a much longer life than 16.10.

---

### Post by RobGoss on 2017-01-02
> **gordintoronto said:**
> It seems like you don't want an update, you want a fresh install. You might as well do a fresh install of 16.04, since it has a much longer life than 16.10.


+1

---

