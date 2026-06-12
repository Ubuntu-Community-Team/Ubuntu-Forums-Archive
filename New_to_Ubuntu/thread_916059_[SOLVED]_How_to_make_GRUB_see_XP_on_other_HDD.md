---
title: "[SOLVED] How to make GRUB see XP on other HDD?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-09-10
I have two HDD's with XP on them, one of the drives is dual booted with Ubuntu. However, it doesnt see the XP on the second HDD. How can I make it see the other OS? 

This was my fault as when it was installing ubuntu, I wanted to be very safe, so I disconnected my second HDD. 

Thanks in advance.

---

### Post by Titan8990 on 2008-09-10
You have to specify that drive to come first in your boot order. Many BIOS have a button to select boot device when booting up.

---

### Post by caljohnsmith on 2008-09-10
> **Lateforgym said:**
> I have two HDD's with XP on them, one of the drives is dual booted with Ubuntu. However, it doesnt see the XP on the second HDD. How can I make it see the other OS? 

This was my fault as when it was installing ubuntu, I wanted to be very safe, so I disconnected my second HDD. 

Thanks in advance.
If I'm understanding your problem correctly, all you would need to do is add the correct entry for Windows in your Grub's menu.lst. Start with:
```
gksudo gedit /boot/grub/menu.lst &
```
And at the bottom, add the following entry:
```
title Windows on 2nd HDD
root [COLOR="Blue"](hd1,0)[/COLOR]
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
The (hd1,0) is the 1st partition of the 2nd HDD, so if Windows is actually on the 2nd partition, it would be (hd1,1), and then 3rd partition would be (hd1,2), etc. If you still have problems, please post the output of:
```
sudo fdisk -lu
```
Let us know how it goes.

---

### Post by lborka on 2008-09-10
Hy Everyone.

I have a somewhat similar problem. I have tried to set up my computer to dual boot Ubuntu 8.04 with xp professional. I have a 160GB HDD partitioned in two on the first partition (20 GB) runs Xp, on the other partition are just files. I have installed Ubuntu 8.04 on a different HDD (20GB)

Ubuntu starts up just fine, grub looks ok, but can't boot into xp I believe probably because I can't see the partition on which the Xp is installed to.

Didn't mention I'm new to Ubuntu.

Here is my menu.lst

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=077ce5f8-5c0e-43d6-8d64-f3fca91d6e0b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=077ce5f8-5c0e-43d6-8d64-f3fca91d6e0b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


and here is my fdsik -l



Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88338224

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2657    21342321    7  HPFS/NTFS
/dev/sda2            2658       19457   134946000    f  W95 Ext'd (LBA)
/dev/sda5            2658       19457   134945968+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31593158

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris


If anyone has any ideas... please help.

---

### Post by caljohnsmith on 2008-09-10
Lborka, exactly what happens when you select Windows from your Grub's menu? Do you get any Grub errors, or do you get some sort of Windows error?

---

### Post by lborka on 2008-09-10
When I select Xp from the list it tries to boot windows, but after a second or two, just returnes to boot menu.

---

### Post by caljohnsmith on 2008-09-10
> **lborka said:**
> When I select Xp from the list it tries to boot windows, but after a second or two, just returnes to boot menu.
That sounds like a Windows-related problem and not a Grub problem at this point. To try and fix the problem, the first place I would start would be to boot up your Windows Install CD, press "r" in the first screen to go to the recovery console, and run the command:
```
fixboot

```
That will make sure your Windows partition's boot sector is OK. Try that and let me know the results and what new errors you might get when booting Windows.

---

### Post by Lateforgym on 2008-09-11
CaljohnSmith,

If I do what you said to get it to recognize XP os on the other HDD, will I still be able to tell it which XP OS to laod automatically?

I ask because I saw a setup on a video site that showed a Ubuntu, XP, Vista setup where it appeared that if he wanted to load Windows, he still had to manually tell it which Windows OS to load

Thanks

---

### Post by caljohnsmith on 2008-09-11
> **Lateforgym said:**
> CaljohnSmith,

If I do what you said to get it to recognize XP os on the other HDD, will I still be able to tell it which XP OS to laod automatically?

I ask because I saw a setup on a video site that showed a Ubuntu, XP, Vista setup where it appeared that if he wanted to load Windows, he still had to manually tell it which Windows OS to load

Thanks
I don't think I understand your question--what do you mean "will I still be able to tell it which XP OS to laod automatically?" Do you mean you want to specify which OS Grub automatically boots if you don't select one on start up? Also, how about posting the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst

```
That will give me a better understanding of your setup.

---

### Post by Lateforgym on 2008-09-11
"Do you mean you want to specify which OS Grub automatically boots if you don't select one on start up?" 

Yes. But I was also wondering if having multiple copies of XP on separate HDDs make auto booting a specific XP OS not possible?

Unfortunately I'm at a coffie house on my mobile so I will not be able to print that info just yet, but I think my answer might clear that up. Please let me know if you still need:

sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by caljohnsmith on 2008-09-11
> **Lateforgym said:**
> "Do you mean you want to specify which OS Grub automatically boots if you don't select one on start up?" 

Yes. But I was also wondering if having multiple copies of XP on separate HDDs make auto booting a specific XP OS not possible?

Unfortunately I'm at a coffie house on my mobile so I will not be able to print that info just yet, but I think my answer might clear that up. Please let me know if you still need:

sudo fdisk -lu
cat /boot/grub/menu.lst
In Grub's menu.lst there is a line that has "default X" where X is some number. Since Grub's numbering begins with 0 and not 1, if you have "default 0" that means the first OS in your Grub menu will be automatically booted once the timer counts down. If you want the 2nd OS in the Grub menu to be booted automatically instead, use "default 1". For the 3rd OS, it should be "default 2", and I'm sure you get the picture. So bottom line is just specify with "default X" which OS in your Grub's menu you want to boot automatically.

If you get everything working, no need to post the output of the commands obviously, but if you need more help then please post them.

---

### Post by Lateforgym on 2008-09-12
Bummer! GRUB looks ok, but now I have a new problem. My MOBO doesnt recognize the second HDD. I noticed the Sata cable was partially out and since sata is hot swapable, I put it back in. The weird thing is Ubuntu sees the drive and the data on teh HDD, but my MOBO (at start up) and Windows does not. 

Im not sure whether to rebuild the raid (stripe 1) or do some sort of error check with Western Digital utilities (if it can see it).

Sigh!

---

### Post by Lateforgym on 2008-09-12
OK, I fixed the problem, my Raid 1(+0) needed to be created again. I almost got it, caljohnsmith, what you said to do worked. However, once I tell it to load the second HDD XP OS, it seems still have the old Windows Boot.ini (dual boot) setup.  Im going to have to edit that out. I'll let you know how it works. Seems that since I yanked the second HDD, GRUB was not in a position to fix the Windows boot.ini. Either way, when I get more time I'll clean up the boot.ini on the second HDD and see what happens.

---

### Post by caljohnsmith on 2008-09-12
> **Lateforgym said:**
> OK, I fixed the problem, my Raid 1(+0) needed to be created again. I almost got it, caljohnsmith, what you said to do worked. However, once I tell it to load the second HDD XP OS, it seems still have the old Windows Boot.ini (dual boot) setup.  Im going to have to edit that out. I'll let you know how it works. Seems that since I yanked the second HDD, GRUB was not in a position to fix the Windows boot.ini. Either way, when I get more time I'll clean up the boot.ini on the second HDD and see what happens.
Did you previously have a Ubuntu Wubi install? That's about the only thing that would have modified your boot.ini file, unless you did it yourself. It's easy to fix though, I would recommend following [Herman's tutorial]("http://users.bigpond.net.au/hermanzone/p9.html") of how to do it. Basically all you have to do is delete the line at or near the end in boot.ini that makes reference to Ubuntu. 

Glad your system is working again though. :)

---

### Post by Lateforgym on 2008-09-12
"unless you did it yourself"

Yes, I did. I forgot that I edited the Windows boot.ini file on the second HDD.

---

