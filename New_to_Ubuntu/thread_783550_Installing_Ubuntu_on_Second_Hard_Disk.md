---
title: "Installing Ubuntu on Second Hard Disk"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by jjascarm on 2008-05-05
I have just installed two new SATA hard disk in my computer and want to install Ubuntu on one of them. I also have Windows XP installed on my existing IDE hard disk.
I formatted the second SATA hard disk using GParted from the live CD, to use for media storage.
I want to install ubuntu on the other SATA drive, but I want to make sure that GRUB is installed on the same hard drive, so that if anything goes wrong I can change the boot order in the bios and still boot from my windows XP hard drive.
Any instructions on how to do this would be greatly appreciated..

Thanks Jason

---

### Post by nottrobin on 2008-05-05
I also would like to be able to do something similar.

Currently I have two hard drives:
200GB IDE -> Ubuntu Hardy Heron
500GB SATA -> Windows XP

I hoped that installing Ubuntu with the 200GB HDD as the primary boot drive would force grub to be installed on its MBR leaving the 500GB hdd alone, but not so. If I try to boot off the 500GB one I get a grub error.

So my question is the same: Can anyone tell me how to ensure that Grub is *only* on the MBR for my Linux hdd? So I can leave the windows hdd's MBR intact?

Ta.

---

### Post by confused57 on 2008-05-05
jjascarm,
   Set the drive you're install Ubuntu to as the first hard drive booted in bios, before you boot up the live cd to install.  Make a note of how the installer/partitioner designates your proposed Ubuntu drive, e.g. /dev/sdc.
Near the end of the install, click on the "Advanced" button in the lower right of the screen, type in /dev/sdc(or however the drive is designated) in place of the default (hd0)...this should ensure that grub is installed to this drive's mbr.

nottrobin,
  Was your Windows drive first in your bios boot order when you were booting just Windows?

I would recommend downloading & burning a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a great utility for repairing OS boot problems.

---

### Post by nottrobin on 2008-05-05
Before I installed Ubuntu I made sure I set the 200GB hdd as the first boot drive. But I didn't do the "advanced" thing cos I didn't know about it.

Now it doesn't make any difference whether I set the 200GB or the 500GB hdd as the primary boot drive, the grub menu displays whatever.

My main Ubuntu partition is /dev/sda1 and my Windows partition is /dev/sdb1. What can I do to remove Grub from my windows drive? Can I simply boot from a windows disk and type "fixmbr" or will that break grub for the linux drive?

Ta,
Robin.

---

### Post by nottrobin on 2008-05-05
I found this article: [http://www.justlinux.com/forum/showthread.php?s=&threadid=130715](http://www.justlinux.com/forum/showthread.php?s=&threadid=130715)
But I don't really understand it. I tried putting the lines it suggested in the menu.lst, but it didn't seem to change anything - apart from add a broken entry to grub called "title Windows installed Master (hd0) now booted from (hd1)".

---

### Post by nottrobin on 2008-05-05
How come super grub disk isn't in the repositories?

---

### Post by confused57 on 2008-05-05
> **nottrobin said:**
> Before I installed Ubuntu I made sure I set the 200GB hdd as the first boot drive. But I didn't do the "advanced" thing cos I didn't know about it.

Now it doesn't make any difference whether I set the 200GB or the 500GB hdd as the primary boot drive, the grub menu displays whatever.

My main Ubuntu partition is /dev/sda1 and my Windows partition is /dev/sdb1. What can I do to remove Grub from my windows drive? Can I simply boot from a windows disk and type "fixmbr" or will that break grub for the linux drive?

Ta,
Robin.

Set your hard drive boot order the same as it was when you were booting Windows normally(before installing Ubuntu), then run fixmbr, using a Windows install disk(a recovery disk won't work).  
Once you get Windows booting OK, reset your hard drive boot order, then boot up the Ubuntu live cd and try installing grub to the mbr of the Ubuntu drive:
```
sudo grub
find /boot/grub/stage1
```
This should return something like "root (hd0,0)", then:
```
root (hd0,0)
setup (hd0)
quit
```
If "find /boot/grub/stage1" shows "root (hd1,0)", then:
```
root (hd1,0)
setup (hd1)
quit
```

If you happen to get "root (hd1,0)", upon reboot, in the grub boot menu, highlight your Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.  This is temporary if it works, but can be made permanent in your /boot/grub/menu.lst.

I was wondering if it's possible that Window's IPL was installed to the mbr of the IDE drive when you were just using Windows?

---

