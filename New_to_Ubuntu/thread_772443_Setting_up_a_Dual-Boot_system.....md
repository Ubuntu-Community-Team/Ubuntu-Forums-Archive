---
title: "Setting up a Dual-Boot system...."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by andybob on 2008-04-28
Hey guys and gals:

Right now I am running XP Pro and I would like to run both that and Ubuntu.  I know I need to create a hard drive partition to install Ubuntu but I have a few questions.

-What is all the Grub stuff I have been reading about?

-So I create a partition, shut down my computer, then run the Live CD, is it as easy as selecting the partition I want to install Ubuntu on?

-What am I missing?

Any help is appreciated....


Andybob

---

### Post by pro003 on 2008-04-28
just leave unpartitioned space as it is - don't create it in windows...

when you boot with live cd, just follow the instructions...

install grub at the end of installation...

that should work fine...

---

### Post by andybob on 2008-04-28
What exactly is "Grub"?

---

### Post by Calash on 2008-04-28
You do not need to create the partition, just free up the space for Ubuntu to use.  Ubuntu will setup at least 2 partitions for it's own use.


Grub is the Linux bootloader that Ubuntu uses.  What will happen during the install is that Grub will overwrite the Windows XP boot loader, but add an entry to point to it so you still can use it.

When you get to the point of installing Ubuntu, pay attention to the screens.  You will want to tell it what space to use.  If you are not careful Ubuntu will overwrite the whole disk...so take your time and read each screen :)

---

### Post by szymon_g on 2008-04-28
personally i would create partition under windows (but, prior to this, i would run defragmentation).
just in case- 5 gb is a reasonable minimum for ubuntu installation and usage.
also (in case when you will wanna use more than this 5gb), seperate / and /home (for users data, eg music etc) is a good idea.

---

### Post by szymon_g on 2008-04-28
Grub is a boot manager.
it lets you choose which system you wanna run.
its config file is in /boot/grub/menu.lst

---

### Post by Zralou on 2008-04-28
First off, DEFRAG windows (2 or 3 times to make sure).  You can create a second partition, or just run the liveCD, install from there and let the install resize windows and use the extra space.

If you do pre partition, use the 'use free space' or 'manual' option during install.

Sara Lou

---

### Post by oedha on 2008-04-28
go to [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu) please :)

---

### Post by Lawrence Talbot on 2008-04-28
Before I switched to Ubuntu, I used to run Mandrake or Suse on a partition.  I decided to buy a second hard-drive and install Ubuntu on it.  I actually like this a lot better.  Ubuntu installed a lot easier than the other Linux flavors and I like the idea of a different hard-drive for a different operating system.  At least it works for me.

---

### Post by muteXe on 2008-04-28
After a defrag or two, I just installed 8.04.   During installation it shows you a bar that represents your hard drive space.  You can you use the slider to say how much of your current windows partition you want to give over to use for your ubuntu partition. I think i chose 20Gb .  Click next, and the installer partitions your disk based on your choices.  This will also automatically create a swap partition for you as well.

---

### Post by andybob on 2008-04-28
Quick question:

Which is better to burn the ISO to?
-CD-R (700 MB)
-CD-RW (again 700 MB)
-or a DVD

Thanks,


Andybob

---

### Post by sayeo87 on 2008-04-28
I don't think it would matter, but whichever one you choose, burn it at a slow (even better, slowest) speed. I've heard others having problems when they burn it at fast speeds.

---

### Post by pro003 on 2008-04-28
c'mon guys, what does it matter what speed... you burn the damn cd - you test it - if it forks - fine... if it doesn't  make another copy - but burning a cd at slower speed does not guarantee you 100% you'll have a successful write.:popcorn:

---

### Post by Zralou on 2008-04-28
> **pro003 said:**
> c'mon guys, what does it matter what speed... you burn the damn cd - you test it - if it forks - fine... if it doesn't  make another copy - but burning a cd at slower speed does not guarantee you 100% you'll have a successful write.:popcorn:

Whatever speed you burn a disk at doesn't guarantee 100% success, however, the slower the burning process, the risk of 'buffer underrun' in some writters without underrun protection is reduced.  If the system cannot send data quick enough during the burn, then errors occur.
Also, if the disk is burned on one machine and used on another, the reading system must be able to read at or above the write speed.  A CD burned at 4x-8x will usually work in most CD readers still alive today.

Having said all that, last saturday I burned 4 ISO's at 48x without a single one showing errors.

Sara Lou

---

### Post by andybob on 2008-04-28
How do you slow the burn speed?

Thanks.

---

### Post by pro003 on 2008-04-28
OK! I'm gonna pass this...:lolflag:

---

### Post by tbrminsanity on 2008-04-28
> **andybob said:**
> How do you slow the burn speed?

Thanks.

It should be an option available to you in the burning program you use.  If your using nero or CD creator then it will choose the optimal speed for you.  If your really worried about it go get one of those 100 CD-R bins so that coasters aren't costing you as much (about $0.005 a CD).

---

