---
title: "Installing Ubuntu as dual boot with XP without GRUB"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by TheIllustriousPotentate on 2008-09-15
Hello, I am a complete beginner to Linux. I looked around, and have found that Ubuntu seems to be the "easiest" Linux distrobution out there. I am not a computer geek, and I am not a comand line user; I'm a point a click user. I want to learn Linux so that I can use the comand line stuff, and "maybe...someday" get rid of Windows. At this time, however, I am not going to get rid of Windows. I know it, it works (for the most part), and any software I would ever want is available for Windows.

I want to partition my hard drive with XP on the first partition, and I want to put Ubuntu on the second partition. I have tried to install Ubuntu, and Grub will partition my drive, install Ubuntu on the second partition, then makes XP completely unacessable. XP shows up in the Grub boot screen, but when selected, the screen goes black, then Grub comes right back up. Ubuntu loads just fine.

I have tried reloading the MBR using the XP disc, and that does not work. Everything I try does not work, so I gave up and just wiped the drive, and reloaded XP. Later I decided to try loading Ubuntu again, but yet again, Grub destroys the MBR of XP, and XP will not load, and is unrecoverable.

Right now, I have (yet again) wiped the drive and reloaded XP. What I want to know, is if there is any way that I can load Ubuntu without Grub. It seems that Grub just will take over the process durring installation. I want to use Partition Magic to partition my drive, and use Boot Magic to boot between XP and Ubuntu. Unfortunately, no matter what I do, Grub just will take over durring the install. How can I install Ubuntu without Grub?

Thank you.

---

### Post by KazPed on 2008-09-15
hey, im a beginner aswell! when i installed ubuntu (the lastest version 8.04 i believe) right before the end, there was a part that said advanced options, and there was a tick-box that said Install Bootloader, and you could choose from grub or another one. i just unchecked that box, and it doesnt install the grub bootloader :)

---

### Post by DrMega on 2008-09-15
That's interesting.

How did you install? I booted from the LiveCD and clicked Install, and let the wizard do the job with pretty much the default options. It installed Grub but the XP option works. That was on Gutsy though (I haven't setup Hardy as a dual boot).

I understand that on Hardy there is a Windows app to sort out the install. I've read of a number of issues with that strategy (can't remember what the issues were though).

---

### Post by KazPed on 2008-09-15
i installed from the live CD, although i wasnt partitioning drives. I have two hard drives to i just installed it onto my spare one. Near to the end, before u start the actual installation is where it says advanced options.

---

### Post by k33bz on 2008-09-15
Ya there is programs that you can use to fix the MBR on the windows side. But there is another disk that you can use as a live cd to repair that disk. I will go look and tell you what that live cd is.



ok it is either "System Rescue CD" or it is "Trinity Rescue Kit"

sorry I dont have the links, you can google it.

---

### Post by egalvan on 2008-09-15
> **TheIllustriousPotentate said:**
> Hello, I am a complete beginner to Linux. I looked around, and have found that Ubuntu seems to be the "easiest" Linux distrobution out there. I am not a computer geek, and I am not a comand line user; I'm a point a click user. I want to learn Linux so that I can use the comand line stuff, and "maybe...someday" get rid of Windows. At this time, however, I am not going to get rid of Windows. I know it, it works (for the most part), and any software I would ever want is available for Windows.

Well, I believe in freedom of choice, and if Windows works, then use it.
I still use XP for three specific apps that are not yet to my liking in Linux. Soon, very soon. :)

> I want to partition my hard drive with XP on the first partition, and I want to put Ubuntu on the second partition.

Completely do-able, and what a goodly percentage of Ubuntu users do.
I've  done this six times, on three desktops, and three laptops.
Perfectly OK


>  I have tried to install Ubuntu, and Grub will partition my drive, install Ubuntu on the second partition, then makes XP completely unacessable. XP shows up in the Grub boot screen, but when selected, the screen goes black, then Grub comes right back up. Ubuntu loads just fine.

Grub is quite intelligent in seeing other installed OS's, including Microsoft product.

It is probable that HOW you install Ubuntu may be the cause of this problem you are having

> I have tried reloading the MBR using the XP disc, and that does not work. Everything I try does not work, so I gave up and just wiped the drive, and reloaded XP. Later I decided to try loading Ubuntu again, but yet again, Grub destroys the MBR of XP, and XP will not load, and is unrecoverable.

Grub does not "destroy" the Win MBR, it merely replaces it with it's own.
And it's just as easy to replace Grub's MBR with a Windows one later.

Second, Grub does NOT touch the Windows partiotion, merely reads it to see what's what. You  would have to explicitly tell the partitioner to mess with the Windows stuff. And yes, I've done that a couple  of times or four... :redface:

> Right now, I have (yet again) wiped the drive and reloaded XP. What I want to know, is if there is any way that I can load Ubuntu without Grub. It seems that Grub just will take over the process durring installation. I want to use Partition Magic to partition my drive, and use Boot Magic to boot between XP and Ubuntu. Unfortunately, no matter what I do, Grub just will take over durring the install. How can I install Ubuntu without Grub?

Thank you.

Yes, you can leave grub off completely, it's in the choices one can make during the install.
But I've never done that, so cannot comment.

As to the Partition Magic LiveCD, I can whole-heartedly recommend it.
It has a more up-to-date GParted than Ubuntu LiveCD's, and it is an entire system in its own right. You can play games and even surf the web while waiting for partitioning or formatting to finish.

A very quick, condensed explanation of how I install Ubuntu to dual-boot...

Shut down XP correctly. Boot XP and defrag. Shut down XP correctly

Boot with Partition Magic. fire up GParted. Shrink XP partition to 10gb.

add the following partitions after the XP Primary partition:

  second primary, 1gb Linux SWAP

  third primary, 1gb named BUFFER

  fourth is an EXTENDED PARTITION. inside this I install Ubuntu partitions

Boot Ubuntu LiveCD and choose INSTALL

Tell the installer to use the pre-defined partitions

Tell Grub to load itself on the MBR of the first drive.


**OK, any comments, ideas, etc are welcome**

---

### Post by TheIllustriousPotentate on 2008-09-15
I have the latest version of Ubuntu (downloaded from the website), and I installed from the live CD.

Hmm. I did notice the check box at the end of the process to install the Grub boot loader. I guess I must have checked that box when installing. I tried everything I could find to fix the XP MBR, but it was just a no go. I know that Windows was still on the disc, and undamaged, but if you can't get to it, then to me, it's classified as destroid.

I have no idea what "Gutsy" and "Hardy" are. I just installed Ubuntu from the live CD that's available from the website.

I do have a second hard drive, and I thought about installing Ubuntu to it, but then I thought....how do I get the computer to boot to the sceond hard drive when I wanted to play with Linux.

Oh well, My computer (XP) is working well once again, and It will be a wile before I play with Ubuntu again. I have to make some back ups first. I had backups that I made using Nero backup, but the backups did not work. Nero sucks.

---

