---
title: "Quin-boot Macbook Pro with Refit, OS X, Windows, Ubuntu - Grub problem"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Luckynkl on 2013-03-23
Hi.  I got a used 2010 MacBook Pro a couple of months ago.  Up until now, I've always used Windows.  I've messed around with Ubuntu a few times, but am pretty much a newbie.  I had a hard time even trying to find terminal, much less know the commands.

Anyhow, I decided to be adventurous and quin-boot my Macbook Pro.  That way I can learn OS X and Ubuntu while still being able to use Windows while I learn.  I used Refit to do the multiple boot.  I have Snow Leopard, Mountain Lion, Windows Vista, Windows XP, and Ubuntu installed.  I can boot into all of them just fine.  But an extra step is required when I try to boot into Windows Vista or XP.  I get the Grub menu whether I hit the Vista, XP, or Ubuntu button on the Refit menu and have to make my selection from the Grub menu.   I don't know how to fix it so that when I click on the Vista button in the Refit menu, it goes directly to Vista instead of Grub.  Same with XP.   Any ideas?

---

### Post by Kevin McCready on 2013-03-23
have you tried Grub From The Ground Up
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by Luckynkl on 2013-03-24
Thanx, Kevin.  I found the documentation a bit confusing tho.

From the Refit documentation I saw this:

[I] If you have both Windows and Linux installed on the same internal disk, and choosing Windows in the rEFIt boot menu boots Linux, the likely cause is that your Linux system installed its boot loader (GRUB, LILO, etc.) in the Master Boot Record (MBR) instead of the partition boot record (PBR). Due to the way rEFIt works, choosing either of the operating systems in the rEFIt menu starts the Linux boot loader installed in the MBR. In the best case that boot loader then presents you with another menu where you can choose between Windows and Linux, and in the worst case it just loads Linux without giving you a chance to get into Windows. 
[/I]
* You can confirm that this affects your system by running the &#8220;Partition Inspector&#8221; application that is on the rEFIt disk image, and is usually installed under /Applications/Utilities. When you run it, it looks at the partitions and file systems on the first hard disk, and generates a report. You are affected if the report contains something like this: *

[I]MBR contents:  
Boot Code: GRUB [/I][I] 

To fix this problem, you need to install GRUB / LILO in the boot sector of your Linux partition instead, then remove it from the MBR. I&#8217;m not aware of a ready-made tool that can safely do that removal. Please ask for help on a Linux forum if needed. [/I]

I ran the Partition Inspector and the MBR contents do indeed show Grub as the boot code.  It says to ask here how to remove Grub from the MBR and install it to my Linux partition instead.  Hopefully without having to reinstall Ubuntu or Windows!  Can anyone show me how to do that?

---

### Post by Kevin McCready on 2013-03-25
I'm not an expert but would experiment after backing up all data. You may not need a tool. I don't know if there is a danger of bricking your machine. Old Fred on this forum seems to be the expert on this.

---

