---
title: "Very new to this and stuck"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by LorenBP on 2013-05-21
I am curious about ubuntu and have installed it as a second boot section.  I installed it through Windows XP and when I boot from ubuntu I get this;

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; Is /dev)
Alert! /dev/disk/by-uuid/A102DD9102DAD6F does not exist.  Dropping to a shell!

BusyBox v1.18.5 (Ubntu 1:1.18.5-1unbuntu4.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

That is it!  I have absoulutely no idea what I am doing but want to have Ubuntu to play with and see if get it and like it.

Can anyone get me booted up?

Thanks,

Loren

---

### Post by Mariane on 2013-05-21
It looks like something went wrong during the install. Try downloading the IMAGE, look up the checksum to see if the image downloaded properly, and if it is OK write it on a CD and install by booting up from that CD. It will also let you play with Ubuntu without installing it, though it is slow when run from a CD.

---

### Post by LorenBP on 2013-05-21
Hi there, thank for the reply.  I have partitioned off an area for the ubuntu and when I boot from the DVD it tells me that there is not enough room (4.3 gb) but I have 20 gb on the dedicated partition.  All else is a green, internet connection and power?  Tried to install that way instead of Mubi (or something like that in windows) but the windows install was all I could do.  Anotherwords it will not me install from my bootable CD with ubuntu on it, is my iso file somehow bad, doubt it and can get into ubuntu from the CD directly.  Just cannot get by the "not enough room" part.  How should I partition the section for ubuntu?

Thanks for your help

(was hoping that with a few commands my dual boot ubuntu might work!)

---

### Post by Impavidus on 2013-05-21
> **LorenBP said:**
> Hi there, thank for the reply.  [COLOR=#ff0000]I have partitioned off an area for the ubuntu and when I boot from the DVD it tells me that there is not enough room (4.3 gb) but I have 20 gb on the dedicated partition.[/COLOR]  All else is a green, internet connection and power?  Tried to install that way instead of **W**ubi (or something like that in windows) but the windows install was all I could do.  Anotherwords it will not me install from my bootable CD with ubuntu on it, is my iso file somehow bad, doubt it and can get into ubuntu from the CD directly.  Just cannot get by the "not enough room" part.  How should I partition the section for ubuntu?

Thanks for your help

(was hoping that with a few commands my dual boot ubuntu might work!)
I assume you created that partition using the windows disk manager or whatever it's called? Ubuntu cannot install to partitions created by windows, how full or empty they may be. Instead you need unallocated disk space or a Linux partition. You can delete the partition and let the installer create a new one.

---

### Post by RockDoctor on 2013-05-21
/dev/disk/by-uuid/A102DD9102DAD6F looks like a Windows filesystem rather than an Ubuntu filesystem. My "solution" when I encounter this type of problem is to boot from a live CD, mount my Linux partition, and comment out the offending line from my Linux installations /etc/fstab file. When booted from the live CD, you might want to execute
```
sudo blkid -c /dev/null
``` to verify the UUID of the windows partition. Hope this helps.

---

### Post by fantab on 2013-05-21
> **LorenBP said:**
> I am curious about ubuntu and have installed it as a second boot section.  I installed it through Windows XP and when I boot from ubuntu I get this;


Is this a WUBI install? What version of Ubuntu are you installing?

Post a screen shot of your partitions from Windows.

---

### Post by LorenBP on 2013-05-21
Hi thanks and the ubuntu parition was a NTFS system.  Do not have access to doing screen shot right now but will try to uninstall Wubi/Ubuntu, delete partition so unpartitioned space and reboot.  After that try Wubi install again, let you know.

Thanks,

Loren

---

### Post by LorenBP on 2013-05-21
Think my version is 12 LTE?

---

### Post by Impavidus on 2013-05-21
Now it's getting confusing. Do you want to install wubi or a full dual boot? If wubi you need a windows (=ntfs) partition, but it doesn't have to be a dedicated partition for Ubuntu. You'll install using the windows installer. If you want a full dual boot you have to make unallocated disk space, boot using the live disk and install from there.
You said that you "Tried to install that way instead of wubi (or something like that in windows) but the windows install was all I could do," so I think you actually wanted a full dual boot. It failed because you had already made a dedicated but unusable partition for it, and therefore you used wubi. But if you delete the partition and install again from the live disk it should work.

Do you still have that wubi (that didn't work properly) on your drive? I think you can uninstall it.

---

