---
title: "[SOLVED] Can I delete GRUB?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by sbonner on 2008-04-30
I initially installed Ubuntu in dual boot mode.  The machine had a partition with the XP restore files, a partition for Windows, a partition for Ubuntu, and a partition for the Ubuntu Swap, in that order.

I quickly decided I could do without XP, but wanted to keep that XP restore partition.  So, I deleted the Windows partition and resized the Ubuntu partition to take up the space.  I still have the XP restore partition.

Now I wonder if I can safely get rid of the Grub boot program.
1)  Does a full Ubuntu install, without partitioning, still load the grub program?  If so, it's probably necessary.
2)  If I just delete Grub, will the machine load Ubuntu, or will it get confused with the XP recovery partition?
3)  How can I remove Grub and still have a good bootup?

I know how to remove options from the Grub menu so I can get rid of mention of XP.  I know how to decrease the timeout function so the menu only runs for a few seconds.  And, I know how to make it run without showing the menu at all (though I'll have to review that one).

What I want is to have the computer skip Grub entirely, saving a few seconds as it goes directly into Ubuntu.  And, I just want to clean up the remains of my earlier experiments.  I don't like inefficiency.

---

### Post by ryot on 2008-04-30
You need grub. You can't boot your OS without it.

---

### Post by ryot on 2008-04-30
[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

---

### Post by Dr Small on 2008-04-30
GRUB does the actual booting. Without it, you won't be able to boot, period.

---

### Post by nhandler on 2008-04-30
Grub is installed in a normal (non dual-boot) installation of Ubuntu as well. You don't want to remove it. If you do, your computer won't boot up. Actually, you probably could remove it. But then you would have to boot up a live cd and tell it to load the os installed on your hard drive. Since I doubt you want to do that, I would leave grub installed.

---

### Post by ptn107 on 2008-04-30
You CAN remove Grub, but you must use LILO as your bootloader then.

---

### Post by caravel on 2008-04-30
You can remove Windows from your /boot/grub/menu.lst and then enable the hidden menu and set a faster timeout.  This means that you won't see the menu unless you hit escape quickly.  This is useful for systems that don't dual boot at all and the only other options would be the recovery mode and the memtest.

---

### Post by bodhi.zazen on 2008-04-30
You can remove GRUB, but you need to replace it with an alternate way to boot your hard drive. 

Options include LILO, the Windows boot loader, GRUB on a floppy, boot from a CDROM, GAG, something ...

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

---

### Post by master5o1 on 2008-04-30
To remove Windows:

What you can do is delete the two Windows partitions (windows backup + windows C:\) and create a partition using their previously allocated space.

Then you can use that partition as a storage place by mounting it as '/home/user/storage' or something.

Just bear in mind that you cannot edit a hard disk while it is mounted, so you should run the partition editor in a LiveCD because then they will not be mounted.

Then you go into /boot/grub/menu.lst and you remove the windows entry from the list of operating systems to load.

---

### Post by jimv on 2008-04-30
You can go fishing with grubs.  They make good bait.

---

### Post by master5o1 on 2008-04-30
Although, to be purely efficient you would have to remove all partitions (delete windows, delete ubuntu) and start over:

My suggestion when you start over is to allocate partitions in a 'sensible' way:

partition 1 should be 250~1000 MB for **swap**
partition 2 should be 10000~20000 MB mounted as **/**
partition 3 should be the rest of unallocated space mounted as **/home**

This keeps your user data completely separate from the operating system, which in turn makes upgrading really easy: Simply cleanly reinstall.
(Your user data + documents will be safe as you do not need to reformat '/home' each time you upgrade/clean install).

---

### Post by ugm6hr on 2008-04-30
> **sbonner said:**
> I know how to remove options from the Grub menu so I can get rid of mention of XP.  I know how to decrease the timeout function so the menu only runs for a few seconds.  And, I know how to make it run without showing the menu at all (though I'll have to review that one).

What I want is to have the computer skip Grub entirely, saving a few seconds as it goes directly into Ubuntu.  And, I just want to clean up the remains of my earlier experiments.  I don't like inefficiency.

There is no inefficiency here.

All OS have a bootloader (even Windows).  You have a choice of which you use.

Given GRUB is already installed, there is little point in using something else.

Just clean up the menu.lst file.

---

### Post by xzero1 on 2008-04-30
You can edit /bootgrub/menu.lst changing the default menu timeout and enable hidenmenu.

menu.lst snippet
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Just change the timeout value and remove # from hiddenmenu

---

### Post by master5o1 on 2008-04-30
I have a feeling that the XP restore partition requires the XP partition to run.

---

### Post by xzero1 on 2008-04-30
> partition 1 should be 250~1000 MB for swap
partition 2 should be 10000~20000 MB mounted as /
partition 3 should be the rest of unallocated space mounted as /home

Why the swap first? I thought hard drives are faster at the beginning of the drive?

---

### Post by master5o1 on 2008-04-30
> **xzero1 said:**
> Why the swap first? I thought hard drives are faster at the beginning of the drive?


Then do it like this:

Partition 1: '/'
Partition 2: '/home'
Partition 3: swap

I just found it easier to define swap and / as specific sizes and then home as what ever was left -- easiest if in the previous order...meh

---

### Post by sbonner on 2008-04-30
Thanks, all of you!  That clears it up.  I didn't know if Grub was the bootstrap, or a secondary program just for dual-boot machines.  I will edit my menu.lst file for maximum efficiency, and be glad Grub is there.

Master5o1, the /home partition idea is intriguing.  I may have to put that in place.  I keep squirreling-up my system by trying things out (new desktops like Kubuntu, new addons, etc), resulting in various failures I then have to fix, and may appreciate being able to reinstall without touching personal files.  I am perhaps a bit too cavalier with this machine.  :)

Can you set the partition to /home via a live GParted disk? (hope I remembered the program's name right)  I seem to remember that being one of the options.  Will I have to change any settings within Ubuntu for it to recognize the partition automatically as the place for personal files?

Thanks for all help!

---

