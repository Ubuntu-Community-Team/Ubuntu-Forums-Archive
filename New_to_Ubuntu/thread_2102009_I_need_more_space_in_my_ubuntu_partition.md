---
title: "I need more space in my ubuntu partition"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by gurrunaki on 2013-01-06
Hi all, I'm running ubuntu 12.04 next to win7 in a laptop toshiba portege z830, I made a small partition for ubuntu, but as long I'm using it I realize that I need more GB in my ubuntu partition. Can I do it from windows just resizing the partitions with some software?
Will affect it to my ubuntu if I resize from windows? 

Thanks in advance!!!

---

### Post by NikTh on 2013-01-06
Hi , 
what you mean when you say > **gurrunaki said:**
>  I'm running ubuntu 12.04 **next** to win7

Have you installed Ubuntu with wubi.exe (from within Windows) or alongside Windows (regular dual-boot from DVD/USB) ? 

I think we will need the existed partitioning schema to help you. 
Boot into Ubuntu and open a terminal (CTRL+ALT+T) , apply the command below and post back here the results
```
sudo fdisk -l
``` [U]
Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read.[/U] [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by grish on 2013-01-06
I think OP means alongside.

---

### Post by mips on 2013-01-06
If Ubuntu is installed to it's own partition (not installed inside of windows via wubi) then boot off you ubuntu livecd/usb stick use gparted to resize your partition.

**BACKUP important documents & files before starting this procedure, there is a always the potential risk of data loss!!! Rather safe than sorry.**

---

### Post by Mark Phelps on 2013-01-06
Do NOT use GParted to resize Win7.  Doing so risks corrupting the Win7 OS and rendering it unbootable.

Instead, use the Win7 Disk Management utility to shrink Win7.  It doesn't have the flexibility of GParted, but it doesn't run the risk of corrupting the filesystem.

---

### Post by mips on 2013-01-06
> **Mark Phelps said:**
> Do NOT use GParted to resize Win7.  Doing so risks corrupting the Win7 OS and rendering it unbootable.


Was not aware of that, have used GParted to resize Win7 NTFS partitions a few times already without problems.

---

### Post by audiomick on 2013-01-06
I can't offer proof, but I have seen numerous posts with the same advice that Mark Phelps gave: use the windows tool to work on windows.

Why not, after all? Boot into windows and de-frag first, which is very advisable anyway if you are going to shrink the partition, and while you're there use the windows tool to work on windows. Makes sense to me, and doesn't represent any significant amount of extra effort.

When you have your free space, boot windows once or twice to give it a chance to run it's disk checks, which is also very advisable according to lots of posts I have seen (makes sense to me too...) then boot into the Ubunut live environment and finish the job from there.

---

### Post by kurt18947 on 2013-01-06
I use another option to work with partitions.  I've been using it for a few years now and haven't been bit yet (touch wood;)).  It's shareware.  I created a boot CD.  When asked if you want to install it, answer "no".  You will then be in work with partitions mode.  I paid for it, installed it and use it in lieu of GRUB or other boot manager.  AFAIK using it for partition work functions without being paid for.  Using it for boot management unregistered shows a nag screen I think.

[http://www.terabyteunlimited.com/kb/article.php?id=544](http://www.terabyteunlimited.com/kb/article.php?id=544)

As the above link states, resizing a linux partition is a two step process.  First resize the partition then resize the file system.  I **assume** this is true using gparted as well but I haven't done it so I'm not certain.  I've resized NTFS partitions - usually shrink them - without using Windows' tools with no issues.

---

### Post by gurrunaki on 2013-01-06
Thanks for all your replies, and sorry doesn't answer before, but family issues...

Here it is the log that Nik ask me for... My biggest doubt is if I resize the hard disk from windows, will I have problems with ubuntu when I will boot on it again? or in windows?

```
@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaac90c7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    81922047    40857600    7  HPFS/NTFS/exFAT
/dev/sda3        81922048   250066943    84072448    7  HPFS/NTFS/exFAT




```

---

### Post by arpanaut on 2013-01-06
Looks like a wubi install to me, the info you need is here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by audiomick on 2013-01-06
Yep.  No Linux partitions there. Must be WUBI

---

### Post by NikTh on 2013-01-06
> **audiomick said:**
> Yep.  No Linux partitions there. Must be WUBI

Yes. Agreed. Wubi install indeed. 
So the biggest space you can have (in wubi install) is 30GB .. if I'm correct (not very sure, but I think is 30GB max) and I don't know if there is a way to resize a wubi installation... 

Consider to uninstall wubi and take advantage of a regular dual-boot .. 

Thanks

---

### Post by Frogs Hair on 2013-01-06
Resizing or moving a wubi root disk is possible , but probably more complicated than backing up and dual booting.[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

---

### Post by gurrunaki on 2013-01-07
Thanks all of you for your answer, my doubt is, if I need uninstall windows as well or how to uninstall completely ubuntu for install again... I don't know...

---

### Post by NikTh on 2013-01-07
> **gurrunaki said:**
> Thanks all of you for your answer, my doubt is, if I need uninstall windows as well or how to uninstall completely ubuntu for install again... I don't know...

Is not needed to uninstall Windows. Just to resize. Resize Windows from within Windows , lot of free tools out there , and leave a space for Ubuntu installation. 

As you installed Ubuntu now , you can uninstall it with 1-2 simple clicks. wubi.exe is just a program like any other program in Windows. So Control Panel > Remove Program > and uninstall Ubuntu. This is easy. 

Be aware that is better to do a defragmentation  of the disk before you resize Windows partition and install Ubuntu.

Lot of tutorials and how to (threads) in here and generally in Web about Ubuntu Windows dual-boot. Search  for "Ubuntu alongside Windows". 

Thanks

---

### Post by audiomick on 2013-01-07
> **NikTh said:**
> ...Be aware that is better to do a defragmentation  of the disk before you resize Windows partition....
Do it in this order. Removing the WUBI install will leave space in your Windows partition, so

Backup any thing you have in the Wubi Ubuntu install
Remove the WUBI
Defragment the windows partition. Maybe twice if you haven't done it for a long time.
Shrink the windows partition with the windows tool.
Boot windows a couple of times to let it run the disk check thing if it wants to.

This will leave you with a space for your Ubuntu dual boot install.

I like to set up my Ubuntu partitions with gparted from the live environment, but you don't have to. I set up a separate /home partition, and I find I have a better overview if I make the partitions first, then install.

If you don't want to do that, run the Ubuntu installer and choose "beside windows".

It shouldn't give you any problems.

---

### Post by gurrunaki on 2013-01-08
I fix it!!! Many thanks to all for your help and advices!!!

What I have done is delete ubuntu from Windows, after that, with a software I fix the partitions, defragment the partition and install again ubuntu with the size that I was looking for.

Many thanks to all of you!!!

---

