---
title: "Ubuntu / Windows"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by govantim on 2008-10-01
When installing ubuntu 8.04 I just put in the cd & went for it, effectively wiping XP media center completely. Now I've been given a copy of XP, how do I go about installing that & keeping ubuntu ???? Hope this aint complicated.  :confused:

---

### Post by nvance on 2008-10-01
Greetings,

Sorry to hear that the drive was formatted, there should have been an option give to you during the install to format/use the whole drive, or partition the disk.
Anyways, what I would do is do a clean install of XP (have XP format the HDD) then do an install of 8.04 and when prompted, make sure to resize the existing partition (should let you drag the slide bar to the partition size that you want).
Once completed, you should get a Grub screen upon reboot that will let you boot into either XP or Ubuntu.

Hopefully that helps.  Someone else might have a suggestion on how to get Windows re-installed with Ubuntu already installed, but I don't trust the Windows install to not wipe the drive again.

---

### Post by lian1238 on 2008-10-01
You need some free space or a partition for Windows to be installed on (you can try to resize the Ubuntu partition.). Windows will format the partition it is to be installed on, unless a Windows is already installed, in which case it will say that it is installing multiple OS on the same partition. Once you've installed Windows, you need to [install grub]("http://ubuntuforums.org/showthread.php?t=224351") again using a LiveCD, because Windows bootloader will not detect Ubuntu. Then you might need to [change the boot drive of Ubuntu in grub]("http://ubuntuforums.org/showthread.php?t=297261").

---

### Post by jrothwell97 on 2008-10-01
Welcome to the Ubuntu Forums!

I'm going to second nvance's recommendation to do a clean install: it should be the most painless way. However, if you're feeling adventurous, there should be a way to retain the Ubuntu installation. Here's how I'd do it:

[list][*]Use the Ubuntu Live CD to shrink the size of your Ubuntu disk partition.
[*]Install Windows in the free space.
[*]Boot into the Ubuntu Live CD again. Open a terminal and run grub-install (you may need to prefix this with sudo).[/list]

I'm not sure if this will work with your exact configuration, so proceed with caution. Your best bet may be a clean install of XP then Ubuntu.

Good luck.

---

### Post by govantim on 2008-10-01
Thanks nvance, I'll be attempting this over the weekend, now got two o/s discs, Ubuntu which I know works and this copy of XP. No matter what happens I'll still have an operating system to install. Thanks again.

---

### Post by govantim on 2008-10-01
Please correct me if I'm wrong. Should I set the computer to boot from cd drive, install windows ( removing Ubuntu ) close, then do the same to re-install Ubuntu but partitioning it :confused:

---

### Post by lian1238 on 2008-10-01
If you're doing a clean install, yes install Windows. You can create a partition for it, leaving free space for Ubuntu. Then you wouldn't have to resize Windows to install Ubuntu, just use the free space for a new partition. You can have different partitions for your Pictures, Music, Videos, etc. if you want. Then in case you do a fresh install of Ubuntu, you can keep your files as they are, and then just mount them. :D

---

