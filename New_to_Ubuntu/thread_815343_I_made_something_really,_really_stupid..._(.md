---
title: "I made something really, really stupid... :("
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ALex! on 2008-06-01
hi! I had a dual boot with vista, then well... my problem is that I erased my Ubuntu partition (including the swap and the ext and all of them) because I wanted to make a fresh install...

so this erased my grub... but my vista partition was still there (with its recovery partition)

when i booted in a live cd, i went to gparted (the one used to edit partition) and i noticed my recovery partition had like 1 gb free, so I decided to resize it so that it had a gig less... then I tried to resize my Vista partition to add this gb... but when it started, i canceled it....

Now gparted won't recognize my vista partition because there appears to be "a problem".... I don't want to delete my Vista partition because I have important files in there.. what should I do???

PLEASE I NEED HELP!

---

### Post by unutbu on 2008-06-01
Burn yourself a TestDisk. This tool may be able to recover your partition, or some of your files.

Here is the homepage: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

TestDisk comes as part of a number of LiveCDs. Here is a list of LiveCDs you could burn:  [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Herman has also written a [guide on how to use TestDisk]("http://www.users.bigpond.net.au/hermanzone/p21.html").

---

### Post by kansasnoob on 2008-06-01
I'd start by recovering the Vista MBR (since you've already removed Ubuntu).

Just discussed this with someone else today:

[http://ubuntuforums.org/showthread.php?t=815204](http://ubuntuforums.org/showthread.php?t=815204)

But, word to the wise ............. you should never, ever, ever use Gparted to resize a Vista partition. I learned this the hard way! Use Vista's own tool! (It's not worth a darn, but it's Vista!)

If you plan on reinstalling Ubuntu you could also just do that which would restore GRUB and then you could choose to boot your Vista OS from the boot screen and see how badly damaged it is. I will have to give Windows credit for having an excellent Restore utility.

---

### Post by ALex! on 2008-06-01
I've tried to recover my MBR with a VISTA DVD, but it didn't work.... :( :cry:

---

### Post by ALex! on 2008-06-01
> **unutbu said:**
> Burn yourself a TestDisk. This tool may be able to recover your partition, or some of your files.

Here is the homepage: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

TestDisk comes as part of a number of LiveCDs. Here is a list of LiveCDs you could burn:  [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Herman has also written a [guide on how to use TestDisk]("http://www.users.bigpond.net.au/hermanzone/p21.html").

but Gparted doesn't recognizes my Vista Partition... and by that I mean it shows an "Unknown" message... It isn't lost at all... :???:

---

### Post by ALex! on 2008-06-01
> **ALex! said:**
> but Gparted doesn't recognizes my Vista Partition... and by that I mean it shows an "Unknown" message... It isn't lost at all... :???:

when i try to install ubuntu via a live cd, my primary vista partition doesn't appear, there is only the recovery partition....

---

### Post by ALex! on 2008-06-01
Is my Vista partition (currently "unknown" by Ubuntu and Vista DVD) lost forever?! do i have to delete it?! :cry: :cry: 

I beg you, anyone... PLEASE HELP :cry:

---

### Post by shifty_powers on 2008-06-01
go and have a look at knoppix. it is a linux distro that is specially designed to be a live-cd, though it can be installed as well, and is well known for being used for it's recovery tools...

---

### Post by shifty_powers on 2008-06-01
[http://en.wikipedia.org/wiki/Knoppix#Popularity](http://en.wikipedia.org/wiki/Knoppix#Popularity)

> Its utilities for system repair and troubleshooting

---

### Post by bgast1 on 2008-06-01
I've always fixed my MBR with a windows 98 disc that I have. Just boot from the CD and type ```
fdisk /mbr
```  at the A: prompt. I've never used Vista (actually never even seen it), would that be an option?

---

### Post by ALex! on 2008-06-01
Please people! I'm a complete newbie! I need REALLY EASY solutions... :( 
sorry!

Thanks in advance...

---

### Post by unutbu on 2008-06-01
ALex!, if I read your first post correctly, GParted was partially through resizing your recovery and Vista partitions. That means it was moving the actual bits that compose one, the other, or both partitions at the time it was halted. 

It is quite likely that file system structure of at least one of the partitions is in a screwed up state right now, and quite likely that it is impossible to recover from this completely. Since you say the LiveCD recognizes your recovery partition, perhaps it had finished resizing the recovery partition and only your Vista partition is screwed up.

The best you can hope for is a partial recovery using something like TestDisk and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec"). PhoteRec comes with TestDisk.

---

### Post by ALex! on 2008-06-01
> **unutbu said:**
> ALex!, if I read your first post correctly, GParted was partially through resizing your recovery and Vista partitions. That means it was moving the actual bits that compose one, the other, or both partitions at the time it was halted. 

It is quite likely that file system structure of at least one of the partitions is in a screwed up state right now, and quite likely that it is impossible to recover from this completely. Since you say the LiveCD recognizes your recovery partition, perhaps it had finished resizing the recovery partition and only your Vista partition is screwed up.

The best you can hope for is a partial recovery using something like TestDisk and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec"). PhoteRec comes with TestDisk.

Yes! you understood me!!! My recovery partition did finish but I stupidly canceled the process of resizing my windows partition!:???:

Could you please give me step by step instructions for using TestDisk?? 

PLEASE, I'd be very thankful...

---

### Post by ALex! on 2008-06-01
Sorry, but I didn't understand Herman's guide... Its difficult for me... :(

---

### Post by HotShotDJ on 2008-06-01
> **ALex! said:**
> Sorry, but I didn't understand Herman's guide... Its difficult for me... :(Alex, perhaps having the instructions in Spanish may be easier for you: [Ejecutando TestDisk]("http://www.cgsecurity.org/wiki/Ejecutando_TestDisk")

---

### Post by ALex! on 2008-06-01
> **HotShotDJ said:**
> Alex, perhaps having the instructions in Spanish may be easier for you: [Ejecutando TestDisk]("http://www.cgsecurity.org/wiki/Ejecutando_TestDisk")

Oh! Thank you! But my problem is that TestDisk "guide" uses some terms I just don't understand... It's not because of the language :???:

But thanks! :mrgreen:

---

### Post by ALex! on 2008-06-01
if this helps... 

I canceled the whole process, when it had just started... 

does this mean I have the chance of having lost just a few files? :(
:cry:

---

### Post by unutbu on 2008-06-01
Post the parts of Herman's guide that you don't understand here, and perhaps we can help explain.

---

### Post by HotShotDJ on 2008-06-01
> **ALex! said:**
> does this mean I have the chance of having lost just a few files?There is a chance that you have lost very little.  Several years ago, I deleted all the partitions from my harddrive, repartitioned, installed a new Operating system, AND used it for several days before I realized that the file backups I had made were bad.

Using TestDisk, I actually recovered nearly EVERY file on one of the overwritten partitions.  What you need to do is start focusing on the solution that we have pointed you toward.  You are correct when you say it is not easy.  If there were an easy solution, we'd tell you about it.  We are not hiding information from you. We've given you all the available information.  It is up to you to implement it.

---

### Post by ALex! on 2008-06-02
So... first I should burn my Testdisk livecd

---

### Post by ALex! on 2008-06-02
and i have a doubt! where will all my "recovered" files be stored in?? :???:

---

### Post by lswest on 2008-06-02
My advice is...fix Vista using vista's tools, not Linux tools.  Boot to your recovery partition and run these commands: ```
chkdsk /f
bootrec /fixmbr
bootrec /fixboot
```
the first one checks for, and fixes, errors.  The second one restores the MBR, the third one adds the correct entries to your bootloader.  This should fix any errors that Vista contain that can be fixed, but i wouldn't be too hopeful, it's never a good idea to stop when resizing something.

*EDIT* since you're already working on the testdisk option, try that first.  Best to restore the files onto an external hard drive/seperate partition on your hard drive.  (mount it to the liveCD).

---

