---
title: "Ubuntu &amp; Kubuntu will not boot, goes to BusyBox?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Steel Frog on 2008-05-28
I dusted off an old machine this weekend to get my girlfriend setup with a nice internet box. It had (I think) Ubuntu 6.06 installed and ran fine.

I got prompted to update to the latest version of Ubuntu. The update process went smoothly until it was time to reboot.

First reboot: The loading/splash screen comes up and loads for about 5 minutes, then I get booted to a plain black screen with white text prompt:

> 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I figured something asploded during the upgrade process which was fine. I dropped in a fresh copy of Xubuntu from a downloaded and burned CD off another machine and after re-formatting the drive and re-installing, the Xubuntu splash comes up, loads 5 minutes and I'm back to the prompt.

What do I do here? I'm still extremely uncomfortable with anything Ubuntu/Xubuntu so I'm really stuck in a loop here!

---

### Post by starcannon on 2008-05-28
I've had this happen when my hard disk wasn't being seen, at busy box I typed:
```

modprobe ide-generic
CTRL-D

```

If that works for your situation you'll want to add that into your menu.lst file as a boot parameter.

Anyway, thats my only advice, GL and keep asking if that doesn't fix it.

---

### Post by Steel Frog on 2008-05-28
Thank you for your reply, starcannon.

Here is what it returned:

> 
[ 1744.009619] ide0: I/O resource 0x3F6-0x3F6 not free.
[ 1744.089661] ide0: ports already in use, skipping probe
[ 1744.089707] ide1: I/O resource 0x376-0x376 not free.
[ 1744.089753] ide1: ports already in use, skipping probe


I'm assuming this isn't the cause of the problem since both checks were skipped.

---

### Post by starcannon on 2008-05-29
You said you dusted off an old machine, just occurred to me you may need to boot with noacpi option I think it is. I'll check back later to see how your getting on, but dig around on that, it is another possible lead for you.

GL

---

### Post by timandjulz on 2008-05-29
I had this happen to me yesterday.  Ended up the UUID on the kernel command line was incorrect.

If this is the case then when you boot, highlight the menu item in grub you are booting to.  Hit 'e' to edit.

Move to the kernel command line.  You will see something like:
/vmlinuz-2.6.24-17-generic root=UUID=(long string) ro quiet splash

Replace the UUID with your hard drive/partition where root is like so:
/vmlinuz-2.6.24-17-generic root=/dev/sda3 ro quiet splash

If that fixes it then edit your /boot/grub/menu.lst file once you get booted.

Cheers,
Tim

---

### Post by Steel Frog on 2008-05-29
> **timandjulz said:**
> I had this happen to me yesterday.  Ended up the UUID on the kernel command line was incorrect.

If this is the case then when you boot, highlight the menu item in grub you are booting to.  Hit 'e' to edit.

Move to the kernel command line.  You will see something like:
/vmlinuz-2.6.24-17-generic root=UUID=(long string) ro quiet splash

Replace the UUID with your hard drive/partition where root is like so:
/vmlinuz-2.6.24-17-generic root=/dev/sda3 ro quiet splash

If that fixes it then edit your /boot/grub/menu.lst file once you get booted.

Cheers,
Tim

I don't get the GRUB boot selection prompt since the only OS installed is Kubuntu so I'm not sure how I could go about and try that.

> You said you dusted off an old machine, just occurred to me you may need to boot with noacpi option I think it is. I'll check back later to see how your getting on, but dig around on that, it is another possible lead for you.
I'll definitely look into that. A quick search did reveal that many people had the some problem I have, but I'm not getting an error message like they are.

---

### Post by timandjulz on 2008-05-29
I haven't installed Kubuntu.  I wonder why they didn't use Grub to give a recovery boot option.  Is there something on the spash screen that lets you choose options?

I wish I could help you.  If grub isn't being used then I have no idea how to control the boot process.

---

### Post by Steel Frog on 2008-05-29
> **timandjulz said:**
> I haven't installed Kubuntu.  I wonder why they didn't use Grub to give a recovery boot option.  Is there something on the spash screen that lets you choose options?

I wish I could help you.  If grub isn't being used then I have no idea how to control the boot process.
No, I don't get any choices really. It just boots up normally to the splash screen and after 5 minutes or so dumps me at the prompt with no error messages or anything.

---

### Post by doorknob60 on 2008-05-29
Pressing escape after the bios does it's thing should bring up grub.

---

### Post by Steel Frog on 2008-05-29
Using escape I tried booting into recovery mode which allowed to to get the following:

> 
Check root = bootarg cat /proc/cmdline
or missing modules, devices" cat /proc/modules/ ls /dev
ALERT! /dev/disk/by-uuid/b238f17a-0377-0483b-8ecb-74a18958f61e does not exist. Dropping to a shell!


It's a standard IDE hard-drive; not RAID or anything. I searched the problem and I couldn't really find an answer.

---

### Post by Steel Frog on 2008-05-29
I can format/nuke the drive if it would help; there's absolutely nothing on it right now other than a non-fonctional Kubuntu installation.

---

### Post by timandjulz on 2008-05-29
Then I was right... it can't find the root partition.  The UUID is great because you can move the drive order around and shift partitions.  But it does make things more confusing when it falls down.

I will defer to someone that knows Kubuntu to say if there is an alternative way to edit the kernel command line.  But if you were able to get a selection for recovery mode then you should also be able to select a normal boot (and thus follow my directions to hit 'e' to edit, etc.)

Alternatively, you can install on another partition on the same HD.  Ubuntu lets you resize the existing partition.

Or... you can reinstall.  :-)

One suggestion I have is to separate /boot from /.  I always use /dev/sda1 for /boot and root goes into /dev/sda2.  That way if something goes wrong I can always reinstall grub and hit /boot without messing up root.

Good luck,
Tim

---

### Post by Steel Frog on 2008-05-30
> **timandjulz said:**
> Then I was right... it can't find the root partition.  The UUID is great because you can move the drive order around and shift partitions.  But it does make things more confusing when it falls down.

I will defer to someone that knows Kubuntu to say if there is an alternative way to edit the kernel command line.  But if you were able to get a selection for recovery mode then you should also be able to select a normal boot (and thus follow my directions to hit 'e' to edit, etc.)

Alternatively, you can install on another partition on the same HD.  Ubuntu lets you resize the existing partition.

Or... you can reinstall.  :-)

One suggestion I have is to separate /boot from /.  I always use /dev/sda1 for /boot and root goes into /dev/sda2.  That way if something goes wrong I can always reinstall grub and hit /boot without messing up root.

Good luck,
Tim
Thank you for your reply.

What's weird about it is that this started happening when I upgraded from Ubuntu 6.06 to Hardy, so I don't think it's something that's Ubuntu/Kubuntu specific. Seems more like a GRUB problem or something.

I did try to re-install Kubuntu yesterday and used the "Use the whole disk, guided" option to install. I figured it would format the hard-drive and start from scratch but it's still doing the same thing.

I'm assuming I must have missed some trivial but important partitioning step hidden away in the Advanced sections or something during the installation. I took a quick glance at the custom partition option but couldn't figure out what I needed to define and in what size (ext3, swap, etc etc).

---

### Post by timandjulz on 2008-05-30
It sounds like your drive order is changing.  In other words when you first install the hard drive is (hd0) or /dev/hda but after install it is (hd1) or /dev/hdb or even /dev/sda.  Before you re-install you might change the boot order in BIOS or switch hard drive connections.

I have been having sound problems so I reinstalled 64bit Hardy on another partition today.  After reboot, my /dev/sda changed to /dev/sdf.  ????  I didn't move anything around either.  Very, very, very odd.  I have decided to stick with the original kernel Ubuntu installs (2.6.24-16 instead of 2.6.24-17).  Everything works with the previous kernel.

---

### Post by ChompTheMan on 2008-05-31
I had a problem similar to yours which was solved in [this thread]("http://ubuntuforums.org/showthread.php?t=813090").  Basically I loaded up the Kubuntu alternate cd and went into recovery mode.  Then I opened up /etc/fstab in vi, copied down the UUID, then changed the UUID in grub to match and everything worked fine.  You don't have to do it this way though becuase in Linux there are many ways to do one thing.  The thread I linked to above has other methods(like mounting root using a live cd then making your changes in a GUI enviroment).  Good luck, hope this helps.

---

### Post by Steel Frog on 2008-05-31
Guess we can drop this issue for now; I spent the day moving my PC into a new case, video and RAM and I'm having all sorts of issues. Neither Linux or Windows will install properly with all kinds of errors.

---

### Post by timandjulz on 2008-05-31
> **Steel Frog said:**
> Guess we can drop this issue for now; I spent the day moving my PC into a new case, video and RAM and I'm having all sorts of issues. Neither Linux or Windows will install properly with all kinds of errors.

Steel Frog, you obviously did something in a previous life and are paying for it now.  Based on the amount of problems, it must have been pretty bad.  I suggest you consider becoming a monk or something.  ;-)

Good luck to you.  :-)

---

### Post by Steel Frog on 2008-06-01
> **timandjulz said:**
> Steel Frog, you obviously did something in a previous life and are paying for it now.  Based on the amount of problems, it must have been pretty bad.  I suggest you consider becoming a monk or something.  ;-)

Good luck to you.  :-)

Hmm, maybe, but this motherboard is definitely some kind of demon-spawn.

---

### Post by flyingtiger on 2008-06-12
> **Steel Frog said:**
> Thank you for your reply.

What's weird about it is that this started happening when I upgraded from Ubuntu 6.06 to Hardy, so I don't think it's something that's Ubuntu/Kubuntu specific. Seems more like a GRUB problem or something.

I did try to re-install Kubuntu yesterday and used the "Use the whole disk, guided" option to install. I figured it would format the hard-drive and start from scratch but it's still doing the same thing.

I'm assuming I must have missed some trivial but important partitioning step hidden away in the Advanced sections or something during the installation. I took a quick glance at the custom partition option but couldn't figure out what I needed to define and in what size (ext3, swap, etc etc).

I have had the same problem but only with the last 3 kernel updates. I upgraded from 7.10 Kubuntu to 8.04. All kernel updates up to 2.6.22-14-generic have booted back to user login without problem. All kernels after 2.6.22-14-generic can't find the boot partition and goes to Busybox.

I have tried every suggestion mentioned in this thread and other suggestions found in other threads and nothing restores to the updated kernel. I have spent a week of spare time running back and forth between my laptop [Dell Inspiron 7000, 384 Mb RAM, 10 GB HDD, combo CDROM/Floppy drive, Ubuntu 4.10 only OS on the HDD] to search for a fix in the forum.

I have resorted to using the last kernel that has been stable for me, 2.6.22-14-generic and will not update to a new kernel until this problem is announced to be fixed on the forum.

This system is Soyo SY-K7ADA mobo, AMD K6 850 MHz CPU, 1 GB RAM, DVD-ROM player, floppy drive, ATI Radeon 128 MB Video card, 70 GB HDD, single OS = Kubuntu 8.04, kernel 2.6.22-14-generic.

---

