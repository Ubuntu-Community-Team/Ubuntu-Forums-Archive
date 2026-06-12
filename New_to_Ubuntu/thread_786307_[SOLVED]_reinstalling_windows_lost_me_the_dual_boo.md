---
title: "[SOLVED] reinstalling windows lost me the dual boot"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-05-08
hey...

i am new to ubuntu. 

I had my drive partitioned as follows:

C: ntfs
D: ntfs
ext2
swap

On the C, I had my windows installed. Note that windows was installed on the system before i installed ubuntu. I then created the ext2 and swap partitions and installed ubuntu.

today, i decided to format C and reinstall windows. Doing so got me to lose the boot loader. So now i can not load ubuntu.

How can I get that back?

I have XP at the moment.

Any help is appreciated.

thanks

---

### Post by DrPppr242 on 2008-05-08
I think you can boot into a live cd mount your ubuntu partition and chroot into it then reinstall grub and edit the grub.conf file.

---

### Post by erfahren on 2008-05-08
See: [Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by newbuntuxx on 2008-05-08
i booted into the live cd and followed the instructions in the above mentioned link. the loader was restored. however, when i choose ubuntu 8.04 from the loader menu, i get the following error message:

Error 17
cannot mount selected partition!

I ran a fdisk -l from the live cd, hope it helps:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27b227b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2           12446       13661     9767520   83  Linux
/dev/sda3           13662       19457    46556370    f  W95 Ext'd (LBA)
/dev/sda4           14360       19457    40949653+   7  HPFS/NTFS
/dev/sda5           13662       14359     5606622   82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

---

### Post by newbuntuxx on 2008-05-08
I also followed the instructions here to the dot:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and got the same results:
Error 17
cannot mount selected partition!

any help guys?

ps. 
find /boot/grub/stage1  

shows:
(hd0,1)

---

### Post by logos34 on 2008-05-08
> **newbuntuxx said:**
> I also followed the instructions here to the dot:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and got the same results:
Error 17
cannot mount selected partition!

any help guys?

ps. 
find /boot/grub/stage1  

shows:
(hd0,1)

Looks like you have a big chunk of empty space between sda1 and sda2, linux root.  Maybe you deleted a partition there?

Boot from the live cd and post your /boot/grub/menu.lst file.

---

### Post by erfahren on 2008-05-08
Ok - take a look at the last post on this thread:
[http://ubuntuforums.org/showthread.php?t=244788](http://ubuntuforums.org/showthread.php?t=244788)

basically - at the GRUB menu you highlight the Ubuntu entry and press the "e" key to manually edit.

change the boot line to read (hd0,1) - remember, it counts starting from "0"
(your first partition is "(hd0,0)" and so-on)

then press "b" to boot

it should boot - then you need to edit the Ubuntu lines in /boot/grub/menu.lst to be (hd0,1) and then in terminal do:
```

sudo update-grub

```
(I just realized I messed up the link in my first post. I apologize for that newbuntuxx)

Edit - logos34 is right - I didn't catch that. I'll leave my post though.

---

### Post by newbuntuxx on 2008-05-09
Thank you very much guys. erfahren's solution worked. 

When I i formatted the ntfs partition, i decided it to shrink it, and free up some space so that I may use it for ubuntu stuff. So, I created a 20 gig ntfs for windows, 50 gigs unpartitioned, 40 gigs ntfs for my back up, and 15 gigs for linux. 

After getting grub to load using the live cd, I loaded grub at boot, and pressed e. i noticed that it was trying to mount: (hd0,2) so i changed it to (hd0,1) and booted. Then i editted /boot/grub/menu.lst and changed all the instances of (hd0,2) to (hd0,1). 

That fixed it.

Now, I must get the internet working on ubuntu again, since i lost it. 

any help would be appreciated guys. 

i opened a thread here:

[http://ubuntuforums.org/showthread.php?t=785422](http://ubuntuforums.org/showthread.php?t=785422)

thanks again guys.

---

