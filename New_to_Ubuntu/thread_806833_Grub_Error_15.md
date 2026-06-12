---
title: "Grub Error 15"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by User X on 2008-05-25
Hey Guys,

I had previously been running 7.10 with a few network problems and wanted to try 8.04.  I have 3 hard drives - two are 200Gb drives with Windows XP on them.  They are being mirrored in a raid array.  The third is where I had my 7.10 installed.  I used windows XP to remove the Ubuntu partitions, and format them into one large NTFS drive.  Everything seemed to work well in windows.  I inserted the live CD and got the Ubuntu desktop.  I ran the install application.  When it finished I was not prompted to take any action so I restarted the PC from Ubuntu. Now where I would normally see Grub loading with an option to choose my OS I get:

GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 15
_


I am pretty new to this so please explain anything I should try pretty thouroughly.  Thanks in advance...

---

### Post by Sarah L on 2008-05-25
This sorta thing tends to happen when a previous Linux bootloader wasn't completely wiped out, and the system tries to boot the older installation - one that no longer exists. Generally, using Windows to format Linux is a Very Bad Idea.

However it's not an uncommon problem: check to see if this post helps you out: [http://ubuntuforums.org/showthread.php?t=297261#4]("http://ubuntuforums.org/showthread.php?t=297261#4")

---

