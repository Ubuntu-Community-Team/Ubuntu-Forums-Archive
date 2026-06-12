---
title: "ubuntu &quot;partition to partition&quot; copy possible?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-08-09
I just got a new hard drive and want to set that one as my primary and keep all my stuff. I'm dual booting with XP and the hard drive comes with a disk that lets you copy from 1 partition to another. But that will only work for the windows partition because i can't access ubuntu's ext3 partition from windows. What is plan to do is:

1. create new partitions on the new drive that match my current ones, but are slightly larger(just in case of anything)
2. once everything is copied, set the new drive as the bootable one
and hopefully it'll run smoothly.

is there a program in ubuntu that could do that?

---

### Post by ByteJuggler on 2008-08-09
First read this thread [here]("http://ubuntuforums.org/showthread.php?t=874643").  Then post back with questions on how you want to proceed, if you have any.  Just to add to that thread:  You can also image single partitions using the same technique as described in that thread, just refer to (for example)/dev/sda1 (the first partition on /dev/sda) instead of /dev/sda (which is the entire disk) in the "dd" commands.

---

### Post by pi.boy.travis on 2008-08-09
Use GParted, a graphical partition manager.  Install it with synaptic or:

sudo apt-get install gparted

Hope this helps!

---

### Post by jordanmthomas on 2008-08-09
You can try this to make things easier:
[http://www.fs-driver.org](http://www.fs-driver.org)

Then your copying software should work in Windows as your ext3 partition will be seen as a native Windows filesystem.

If you want to go the route you've suggested, try gparted (available as its own livecd or on the Ubuntu LiveCD).  It'd probably be best to run it off a LiveCD if you're copying a live filesystem since /proc and /dev won't be populated (a good thing, you don't really want to copy them)

---

### Post by st33med on 2008-08-09
> **pi.boy.travis said:**
> Use GParted, a graphical partition manager.  Install it with synaptic or:

sudo apt-get install gparted

Hope this helps!

Using gparted while on the hard disk is a bad idea. You might want to use the [Gparted LiveCD]("http://gparted.sourceforge.net/download.php").

---

### Post by bpowell2005 on 2008-08-09
> **waggingwabbit said:**
> I just got a new hard drive and want to set that one as my primary and keep all my stuff. I'm dual booting with XP and the hard drive comes with a disk that lets you copy from 1 partition to another. But that will only work for the windows partition because i can't access ubuntu's ext3 partition from windows. What is plan to do is:

1. create new partitions on the new drive that match my current ones, but are slightly larger(just in case of anything)
2. once everything is copied, set the new drive as the bootable one
and hopefully it'll run smoothly.

is there a program in ubuntu that could do that?

Looks like you have lots of suggestions here...I've cloned a Windows driver from smaller to larger using a liveCD called "Clonezilla"...it also has GParted on it...just hook up both drives, boot into CloneZilla and follow the prompts...the smaller drive will be cloned exactly onto the larger one...you can then reboot the same liveCD, and boot into Gparted, from here you can resize the partitions as you see fit...then just plug that larger drive in as the master, and reboot from the hard drive...you'll be in business!

---

### Post by cdtech on 2008-08-09
Personly I would use the "gparted" cd to format and configure the new drive in question. You can create resize and format each partition to your taste and even create a boot sector for your MBR (boot flag). Then I would use "dd" on a command line to copy all of the information from one partition to the new partitions. This will copy the information but not remove it from the original location (in case you need to boot from the original).

While using the "live cd" (after the transformation) you could even "update-grub" and configure your "/etc/fstab" file for the new "/dev" paritions.

**P.S.**
See my signature on using the "dd" command.

---

### Post by waggingwabbit on 2008-08-09
crap....maybe i'm missing some steps. i looked at a few different methods and decided it was easier to just use gparted that came with ubuntu 8 CD. It was easier to keep the partitions the exact same size that way (I type in 30,000 for a 30gb partition, and it comes out as 29.xx or something) which I read in one of the guides was the best thing to do. After it was done copying, I set my new HD to boot, and it says "can't load OS" or something close to that. it didn't even load grub...that was the only message i got, so I don't know if it was talking about windows or ubuntu. 

also, on my original HD, windows doesn't load up anymore. when i pick XP from the grub menu, I get a message saying files are missing or curropted from some windows directory and tells me to load up the windows CD and press "r" for the recovery console. No further instructions given to me. I typed in "help" and see "fixboot" and "fixmbr". I ran the first one, the second one said theres a chance it could mess up all the partitions and I don't be able to load up anything anymore, so i decided against running that...still can't load up XP.

---

### Post by pi.boy.travis on 2008-08-09
DON'T run fixboot or fixmbr!!!  That will destroy grub and make it impossible to access Ubuntu!

---

### Post by cdtech on 2008-08-09
> **pi.boy.travis said:**
> DON'T run fixboot or fixmbr!!!  That will destroy grub and make it impossible to access Ubuntu!

That's not totally true. You can use the Live CD to access Ubuntu and repair the Bootloader.

If you want to do away with Ubuntu, you would "fixmbr" on Windows. It will say that but it will do nothing but repair the Boot sector on the windows partition, allowing you to boot right into Windows. If you want to keep Ubuntu then just boot the Live CD and repair your GRUB Bootloader that way.

---

### Post by DGortze380 on 2008-08-10
> **waggingwabbit said:**
> (I type in 30,000 for a 30gb partition, and it comes out as 29.xx or something) 

Follow the suggestions below for fixing windows mbr and reinstalling grub... but I had to be obsessive and clarify that this is because there are actually 1024mb == 1gb. 

So 30,720mb == 30gb

---

