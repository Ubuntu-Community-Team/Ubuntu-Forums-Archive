---
title: "gpart  erased vista"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by jethro amalgamation on 2008-08-12
So i am dual booting with vista and ubuntu 7.10. I originaly repartitioned a space for ubuntu with vista disk manager. I decided that i wanted to shrink ubuntu and set up a seperate partition for grub using gpart. 

When i opened gpart it did not show any partitions so i had to start from scratch. I am pretty sure that this is where i went wrong and erased the whole hd when i repartitioned a section for grub. 

Now when i open my computer grub does not load and i get an error 22. 

I tried to repair with my vista recovery disc but all that shows up in the repair menu is my ubuntu partition.

Am I totally screwed? or is there a way to recover my vista and or ubuntu files?

---

### Post by bumanie on 2008-08-12
Your best chance of recovering what has been lost is to use testdisk or photorec, both available from [here]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by markjensen on 2008-08-12
+1 on the "testdisk" app.  It does a great job of looking at the data areas and determining what partition(s) exists, if you ever accidentally remove one or such.

Secondly, an observation.  You stated you originally partitioned space with Vista's manager.   I am a big fan of using the right tools for the job.   I recommend using Vista's built-in parititon manager when working with Windows partitions.  But if you are doing something for Linux, it is probably not the best tool.

Then, when your Linux g/qt/parted tool showed an empty drive, or other nonsense, that should alert you that **somthing is not right** and you should stop and diagnose immediately.

I wish you luck in recovery, but the additional writing you have done may have caused significant damage. :(

---

### Post by jethro amalgamation on 2008-08-12
Alright i am going to give testdisk a go, will report on success. Thanks for the help so far.

---

### Post by markjensen on 2008-08-12
On a test system that I completely removed all partitions, testdisk was able to determine a working partitioning scheme and restore the computer to operation.   The original configuration used an extended partition, and testdisk's solution made them all "primary", but it was equally valid.  (testdisk seems to want to fill the primaries first, then add in extendeds)

Note, in this case, I just removed the partitions - and did not make further changes or writes to the drive.  Doing that will lower the odds of recovery, obviously.

---

### Post by indytim on 2008-08-12
After the dust settles and, hopefully, you are able to recover your partition data properly, do yourself 2 big favors:

1.  Get a copy of GParted Live at [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php").
2.  Boot to this tool for future partition work.  You'll eliminate the guesswork associated with the active partition and you have complete control over whatever partition work you want to achieve.

IndyTim

---

### Post by jethro amalgamation on 2008-08-12
burned the livecd for test disc on another computer and tried to load it on broken computer and the disc will not load. Also tried gparted live cd will not work. I can only load the ubuntu live cd. is there anyway i can use testdisc from here?

---

### Post by bumanie on 2008-08-12
Yes, there is: > sudo apt-get install testdiskOnce it has installed, type testdisk into terminal to start it, not sure if photorec is included in ubuntu or not. Don't get put off by it's name, it does not only 'look' for jpeg's etc., it seeks out most file types including text etc. if testdisk doesn't work, try photorec, it reads off the 'raw disk' and is filesystem independant.

---

### Post by bodhi.zazen on 2008-08-12
Yes, testdisk in in the repositories.

Either :

```
sudo apt-get install testdisk
```

Or use Synaptic.

You may need to add some repositories first (I think test disk is in universe).

[uhelp]community/Repositories/Ubuntu[/uhelp]

---

### Post by jethro amalgamation on 2008-08-13
So I think I am way over my head here. I got test disk to run and did an analysis and it did not report any other errors other than there are no bootable disks. 

I dont really understand the naming system of logic partition, primary partition, etc..

I am figured out which partition prob has my files on it because it is mostly full, there are 4 other partitions that are empty for the most part. 

the one that is mostly full, do i change that to my primary bootable or my primary?

or should i just throw in the towel at this point

---

### Post by bodhi.zazen on 2008-08-13
Well, it depends on how valuable the data is and how much time you have.

You should be able to recover with a little reading, should not be too hard.

Take a look at this : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

And these links on testdisk :

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)

Now , if you get stuck, ask. Be sure to post a little more detail ...

You can set a bootable flag on a partition very easily with gparted or fdisk.

---

### Post by Zalbor on 2008-08-13
You wrote gpart... Did you mean gparted and just didn't type the entire name, or do you actually mean gpart? gpart is a very different program from gparted...

---

### Post by Shazaam on 2008-08-13
1. Boot the Ubuntu livecd
2. Go to Applications>Accessories>Terminal
3. In the terminal widow that opens type in...
```
sudo fdisk -lu
```
(lowercase LU)
and find a way to post back the output here. The fdisk code will print out a list of your drive(s) and partition(s). We will need all info including asterisks (they show the bootable flag) like this...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   620526689   310263313+   5  Extended
/dev/sda5             126    12546764     6273319+  82  Linux swap / Solaris
/dev/sda6        12546828    53817749    20635461   83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   301764959    82839141   83  Linux
/dev/sda9   *   301765023   461145824    79690401   83  Linux
/dev/sda10      461145888   615112784    76983448+  83  Linux

```

---

### Post by jethro amalgamation on 2008-08-13
ok here it is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      160650    67280219    33559785    c  W95 FAT32 (LBA)
/dev/sda3       227432205   307323449    39945622+   f  W95 Ext'd (LBA)
/dev/sda5       227432268   303965864    38266798+  83  Linux
/dev/sda6       303965928   307323449     1678761   82  Linux swap / Solaris

---

### Post by Shazaam on 2008-08-13
> **jethro amalgamation said:**
> ok here it is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      160650    67280219    33559785    c  W95 FAT32 (LBA)
/dev/sda3       227432205   307323449    39945622+   f  W95 Ext'd (LBA)
/dev/sda5       227432268   303965864    38266798+  83  Linux
/dev/sda6       303965928   307323449     1678761   82  Linux swap / Solaris

Looks like Vista "might" be gone. At least your Recovery partition is there. While still running the Ubuntu livecd, go to Places>Removable Media, look in sda2 and sda3 (they won't be labled as such) and see what is there.
I don't know the sequence for Vista but we will probably end up repairing the mbr with your Vista disks.
I have to go run some errands but I will be back later. Hopefully someone will step in and help you.

---

### Post by jethro amalgamation on 2008-08-13
so for some reason my live cd does not have an option in places for live cd. 

I went to my computer and there is my ubuntu files titled disk-1 and then there is another disk with a bunch of unreadable files. Is it possible that this is my windows partition?

---

### Post by Shazaam on 2008-08-13
Quite possible or it is the Recovery partition and not Vista. You have a few choices-
1. Use a SuperGrubDisk (burnt to cd) to boot the Ubuntu partition and browse/recover those Windows files.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
2. Sending/taking the pc to the original vendor/manufacturer for repair (may be covered under warranty).
3. Use testdisk as stated before to try to recover a previous working partition table.
4. Use your Vista disk(s) to try to either "fixboot" or "fixmbr" (using the Recovery Console).
5. Try to re-install Vista using the disk(s) and Recovery partition (maybe loosing saved Vista/Ubuntu files)
6. Complete wipe of the drive and installing the operating system of your choice. If you do this you will need to purchase a retail version of Vista/XP etc. Most linux distro's are free.

I have used testdisk before, make sure you read as much about how to use it before taking the plunge. You can either be successful in restoring the drive; or you can at least be able to recover critical files that you need and back them up to a cd or a usb drive.

---

### Post by nicedude on 2008-08-13
I was about to post here that you were sunk, then I googled to learn how dell their recovery partitions and found out that they use FAT32 to hold the data and they use a symantec utility to effect the recovery. So sda1 is the utility and sda2 is the data ( but man they took alot of your disk to do this with, I hate this type of cheapness ). Here is a link to a guy who has a website about this

[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

Normally you could reboot your computer and press CTRL+F11 to automatically go back to the factory configuration, but I would not try it right off as from this nice mans website I see that modifying the disks MBR ( master boot record ) can cause this recovery to fail, and Ubuntu or any other linux does overwrite the MBR with GRUB bootloader code. On this website there are instructions to try and restore your machine even if you have done something to MBR so go to it and read up before trying anything. Here is a link to the recovery part of the website where he explains this. 

[http://www.goodells.net/dellrestore/fixes.htm](http://www.goodells.net/dellrestore/fixes.htm)

Post back here or PM me if you need help implementing what he says to do.

Goodluck, and hope this helps

---

