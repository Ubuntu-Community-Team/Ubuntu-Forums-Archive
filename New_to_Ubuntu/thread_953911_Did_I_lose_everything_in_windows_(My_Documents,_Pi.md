---
title: "Did I lose everything in windows (My Documents, Pictures)"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by laflair13 on 2008-10-20
Hey all, I installed ubuntu last night and I did it as a partition but I cannot seem to find my documents from windows anywhere.

I read a few threads and did a terminal sudo fdisk -l  and this is the return

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14880   119523568+  83  Linux
/dev/sda2           14881       30401   124672432+   5  Extended
/dev/sda5           30049       30401     2835441   82  Linux swap / Solaris
/dev/sda6           14881       29695   119001424+  83  Linux
/dev/sda7           29696       30048     2835441   82  Linux swap / Solaris

Partition table entries are not in disk order


Please tell me I can do something to get my documents. I have a ton of scripts, applications and kids pictures that I do not want to lose.

If anyone can point me in the right direction so I can find these and transfer them over to ubuntu, It would be very appreciated.

Thanks

---

### Post by LowSky on 2008-10-20
well it seems like your Windows partition is gone but you might get something back take a look at this

[http://www.getbackdata.net/](http://www.getbackdata.net/)

---

### Post by hyper_ch on 2008-10-20
you don't make regular backups?

---

### Post by laflair13 on 2008-10-20
I do make backups like once a month, but havent in a few months, so I am losing a good portion of stuff.

I tried that data recovery program but I have no clue how to use it and dont understand what the mean by "image" Where would I find that at?

---

### Post by estyles on 2008-10-20
It definitely looks like you clobbered your windows partition, which is why it's a good idea to back stuff up before installing a new OS.

Here's what I would do to try and get it back...  Boot up a LiveCD.  Once you're booted to Ubuntu on the LiveCD, open up Firefox and search for testdisk.  Then use testdisk to try and recover your old Windows partition.

You'll need to install testdisk, because it's not included on the LiveCD, but it is easy enough to get.  Just open up a terminal and type "sudo apt-get install testdisk".  Although you're better off doing a search (either on this forum or with Google) rather than following my instructions.

You *should* be able to use testdisk to restore your Windows partition.  You're then going to want to backup any data you can get at, as you will probably need to reinstall Ubuntu if you still want to use it, and you may need to reinstall Windows as well.  (I'm assuming at this point that you're not too worried about anything on the Ubuntu partitions, since you may need to kill those partitions in order to get at your Windows partition.)

Assuming that testdisk finds the partition alright, you should be able to get at and backup the data without having to reboot at any time.  You'll just go to the disk in question and look for \Documents and Settings\username\My Documents\.

Hope this helps, and good luck.  Avoid using the computer in any way other than with a LiveCD until you've either recovered the data or given up, as your chances of recovering the data dwindle the more you overwrite it.

---

### Post by WRDN on 2008-10-20
It is much easier to recover data from an NTFS or FAT32 partition (that Windows was/ is installed on), than a different filesystem. Please, do not boot from the HDD, until you have [attempted] to recover some/ all of the data. This is to ensure the sectors where the data was stored are not written over more. Instead, I would advise running from a LiveCD, as this ensures data is not written to the HDD (as no partition is mounted automatically). You may consider [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") for recovering the data.

---

### Post by laflair13 on 2008-10-20
I installed the test disk, Now I just dont see where to run it from. A friend of mine was helping me but he had to leave for a while and I am brand new to ubuntu.

---

### Post by estyles on 2008-10-20
> **laflair13 said:**
> I installed the test disk, Now I just dont see where to run it from. A friend of mine was helping me but he had to leave for a while and I am brand new to ubuntu.

You just type "testdisk" in the terminal.  Actually, that should probably be "sudo testdisk".  You may have a tough time using it until your friend comes back...  it's not the simplest program to use, but when you're trying to restore a deleted partition, there's not really a simple solution...

---

### Post by laflair13 on 2008-10-20
I do see this line when I ran the test drive.

  HPFS - NTFS           1111   0  1 30399 254 63  470527785 [HP_PAVILION]


That is what I had before I installed ubuntu, Hopefully I can get some data from that. If I can figure out how to restore it.

Thanks for your help. Hopefully I dont break this thing more than what it is.

---

### Post by estyles on 2008-10-20
I'm assuming you don't care if you break Ubuntu (you can always run the LiveCD in order to get at your hard drive, and can reinstall once you get your data back).  In that case, you want to enable that HPFS partition, even if it means disabling other drives.  I don't use testdisk frequently, but I did use it once when I accidentally deleted all my stuff, so I know that it's not terribly intuitive, but there are pretty good step-by-step instructions to be found, possibly on that wikipedia page that WRDN linked to.

---

### Post by laflair13 on 2008-10-20
It came up with this and I have no clue which one to chose.

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,


Has me lost. I dont want to pick one and mess it up, Can you point me in the right direction.

I hate to keep bothering but I am sure you know what I am going through since you did it yourself before.

I am more worried about the pictures, My wife is going to kill me if I cant get them back....lol

Thanks for all your help.

---

### Post by estyles on 2008-10-20
Sorry, you posted that while I was on my way home from work.  As much as I'd like to help you, I am far from an expert at using testdisk.  Your best bet is to check the wiki or the man page for testdisk.

If you want my advice, you want to scroll down to the Windows partition and press Right Arrow until it says P, preferrably with a '*' next to it.  I suspect that it won't give you a lot of choices.  If you cannot make it a 'P', then an 'L' will work, although make it a 'P' if you can.  If you want any more advice, don't hesitate to ask, although the wiki or documentation is probably more helpful here.

Sorry I can't be of more help.

---

### Post by laflair13 on 2008-10-20
I have no ideal what I did, but I reinstalled ubuntu and I got all my window files back, Even down to the firefox bookmarks.

Thats one thing I am glad happened.

Thanks again for all your help. It was very much appreciated.

---

### Post by estyles on 2008-10-20
> **laflair13 said:**
> I have no ideal what I did, but I reinstalled ubuntu and I got all my window files back, Even down to the firefox bookmarks.

Thats one thing I am glad happened.

Thanks again for all your help. It was very much appreciated.

:shock:

That didn't seem very likely...  I mean that you could go through that, not know what you've done, and miraculously get everything back...

=D>  Oh well, congrats!

BACK IT UP, NOW!!!

---

### Post by bpowell2005 on 2008-10-21
> **estyles said:**
> :shock:

That didn't seem very likely...  I mean that you could go through that, not know what you've done, and miraculously get everything back...

=D>  Oh well, congrats!

BACK IT UP, NOW!!!

I'll second that; do a backup!

I've installed Linux onto a drive with Windows already there several times, and never had a problem...but I always have a nervous feeling when resizing partitions on a drive with a OS already on it...so I'm always mindful about backing up data before I start playing with partition tables.

I'm glad you got your files back...good luck!

---

### Post by stalkingwolf on 2008-10-21
The old saw , " check twice, install once" seems to apply.

---

