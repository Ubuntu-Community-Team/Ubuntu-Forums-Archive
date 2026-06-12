---
title: "Recover from 'Disks' mis-use"
date: 2016-06-19
forum: New to Ubuntu
---

### Post by BrianV on 2016-06-19
I have used Ubuntu for some time, but am acting like a new user.

My system has two 80 GB hard drives, one with the Ubuntu system and another partition of about 40 GB for storage. The other drive has miscellaneous Windows relate stuff that I haven't done anything with. Until I messed things up, Nautilus showed the 40 GB partition and the 80 GB separate drive. I used 'Disks' to try to recover a USB pen drive that wasn't working but my error was to be working on the hard drive instead. I attempted to clear the partitions on that drive and, fortunately wasn't allowed to mess up the Ubuntu partitions. However, I have made the 40 GB partition on that drive invisible to the system.

Rather than get deeper in a hole, I'm looking for help. This partition has a large number of photos on it, a few of which I cannot recover from backup, so being able to recover data after reconnecting the missing partition would be very desirable.

---

### Post by yancek on 2016-06-19
I'm not sure I understand.  You were trying to change partitions on a flash drive and incorrectly changed them on the 40GB drive with your data, is that correct?  If so, stop using that disk and download testdisk to Ubuntu and make sure you read the detailed instructions on the web site.  If this isn't the problem, post more specifics.

---

### Post by grahammechanical on 2016-06-19
You may also need the companion software to Testdisk - PhotoRec

You will need space to out the recovered files to. So, you may want to think about making at least 40 GB of space available of that other 80 GB drive. Or you can be selective of the files types you recovery. Only going for those image files.

[URL="http://www.cgsecurity.org/wiki/PhotoRec"]http://www.cgsecurity.org/wiki/PhotoRec

[/URL]

---

### Post by BrianV on 2016-06-20
Yes, that's pretty accurate: I thought I was reformatting the USB stick, but instead was trying to reformat the hard drive. The hard drive, as I recall, showed up as two major partitions, each about 40 GB. The first was where I stored photo,etc. and the second seems to be further divided into Linux and Linux Swap partitions.

Here is what testdisk indicates:

/dev/sda   - 80 GB / 74 GiB - CHS 9729 255 63

Partition            Start                 End                 Size in sectors
-------------          ----------------        ----------------       ---------------------
HPFS - NTFS   011                   5307 254 63     85272957

Linux                5307 215 29      9541 199 2       68018176

*Linux Swap     9541 231 35       9729 7813        3010560


I'm not clear what to do next?

---

### Post by yancek on 2016-06-20
The TestDisk people have a step by step tutorial at the link so read through that before beginning.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by BrianV on 2016-06-20
The results I sent are after following the testdisk step-by-step up to "Quick Search". It seems to inicate it found 3 partitions, with Linux Swap Primary Executable. I thought the Linux partition would be Primary Executable and Linux Swap and HPFS - NTFS would be Logical. Without a better understanding of what I'm doing, I'm reluctant to start any more changes.

---

### Post by sudodus on 2016-06-21
***Work on a cloned copy***

If you want increased safety, please get a new drive of at least the same size as the damaged one, and clone the content to the new drive.

Then you can use the trial and error method with ***testdisk*** on the cloned copy. If it fails, you can clone from the damaged drive again and try something else :-)

This method is particularly good for drives with failing hardware (bad sectors or memory cells), but it is useful in your case too, in order to find a working method to repair your partition table and file systems without taking risks with [the data in] the original drive.

-o-

The program ***ddrescue***, that comes with the package gddrescue is good for this cloning process.

```
sudo apt-get install gddrescue
```

There is a good description in the info page

```
info ddrescue
```

---

### Post by BrianV on 2016-06-21
Thank you for the advice. Cloning the drive to safely experiment seems the best next step, but I won't be able to get to that for the next few months, so I'll mark this thread 'solved' and perhaps re-open it in the fall.

---

### Post by sudodus on 2016-06-21
Then you will be welcome back :-)

---

### Post by BrianV on 2016-10-25
I am back, with an external drive, and hope you can provide further help, Sudodus.

I have downloaded gddrescue and looked at the info page. Also have rerun testdisk, with slightly different results. It lists an executable Linux partition and a small primary Linux Swap partition, but no longer lists the the HPFS - NTFS partition: the block up to 5307 215 29 doesn't list at all.

I can't see how to use gddrescue, so perhaps you can help with that. Do I need to run from a Ubuntu disk image in order to copy the corrupted hard drive, since it contains the OS? What gddrescue commands do I need to copy the whole /dev/sda hard drive?

Hopefully you can help me get to the stage of having a clone and allow further experiments without causing further havoc to my main drive.

Thank you for helping.

---

### Post by sudodus on 2016-10-25
You can work according to ***Example 1 in the tutorial*** of

```
info ddrescue
```

> 7 A small tutorial with examples
********************************

This tutorial is for those already able to use the dd command. If you
don't know what dd is, better search the net for some introductory
material about dd and GNU ddrescue first.
...
Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to
/dev/hdb.
Note: you do not need to partition /dev/hdb beforehand, but if the
partition table on /dev/hda is damaged, you'll need to recreate it
somehow on /dev/hdb.

     ddrescue -f -n /dev/hda /dev/hdb logfile
     ddrescue -d -f -r3 /dev/hda /dev/hdb logfile
     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1
     e2fsck -v -f /dev/hdb2

This is slightly old and you are using Ubuntu , so the two ddrescue commands should be changed to

```
sudo ddrescue -f -n /dev/sdx /dev/sdy logfile
sudo ddrescue -d -f -r3 /dev/sdx /dev/sdy logfile
```

where sdx is the source drive and sdy is the target drive.

Boot from a live USB drive. You cannot be sure in which order the drives will be found and given drive letters, so you must check it manually, and double-check, so that you get it correct. Otherwise you might overwrite the drive with your data, and all data will be lost. Use the following commands to identify the drives:

```
df -h
sudo lsblk -fm
sudo parted -ls
```

Let us assume that your source drive will be sda, your target drive sdb and your boot drive sdc. In that case you can write the logfile into the live drive, but if you want to be sure it survives a reboot, you should write it into a fourth drive or make a persistent live drive.

```
sudo ddrescue -f -n /dev/sda /dev/sdb "/path-to-directory-the-survives-a-reboot-in-live-drive-or-a-fourth-drive/logfile"
sudo ddrescue -d -f -r3 /dev/sda /dev/sdb "/path-to-directory-the-survives-a-reboot-in-live-drive-or-a-fourth-drive/logfile"
```

Notice that the names can be in another order for example that the target drive is /dev/sda and the source drive is /dev/sdb, so it becomes

```
sudo ddrescue -f -n /dev/sdb /dev/sda "/path-to-directory-the-survives-a-reboot-in-live-drive-or-a-fourth-drive/logfile"
sudo ddrescue -d -f -r3 /dev/sdb /dev/sda "/path-to-directory-the-survives-a-reboot-in-live-drive-or-a-fourth-drive/logfile"
```

The cloning might take a very long time, maybe days and nights. After tha cloning, I suggest that you shut down your computer and remove the source drive - do as little as possible with it.

You should do the recovery attempts on the target drive, and you can test several tools. You mentioned ***testdisk***. If it does not work you can try ***photorec*** from the same developer. ***photorec*** can recover files even without a file system by identifying the data on the disk. But the file names and directory structure is lost and it is hard work. In other words, it is worthwhile to try a lot with testdisk before giving up.

---

### Post by BrianV on 2016-10-25
Thank you. Sounds like I have some careful work to do. Will report as progress is made.

---

### Post by sudodus on 2016-10-26
I edited my previous post (the suggested command lines: "/path-to-directory-the-survives-a-reboot-in-live-drive-or-a-fourth-drive/logfile"), but for some reason no comment about the edit is showing. Anyway, the command lines seem correct now.

---

### Post by BrianV on 2016-10-26
I have booted from a live USB and run the commands to identify the mountings. My corrupted hard drive is /dev/sda, with sub directories sda2, sda5, and sda6. sda is show as size 74.5G, sda2 as 1K, sda5 as 32.4G, and sda6 as 1.4G.
The destination drive, a Seagate Backup Plus Drive, is /dev/sdd.
My other 80G hard drive is /dev/sdb, with more than 20G free space, so that should be usable for the logfile.
I have attached screen shots of the terminal session, or tried to.

It appears my gddrescue command should be:

sudo ddrescue -f -n /dev/sda /dev/sdd "/dev/sdb/logfile"
sudo ddrescue -d -f -r3 /dev/sda /dev/sdd "/dev/sdb/logfile"

Does that seem reasonable? What further commands do I need to initiate the copying?

---

### Post by sudodus on 2016-10-26
No, don't write the logfile to the block device. You should write to the mount point, where the the partition with 20 GiB free space on drive /dev/sdb is mounted. The actual hexadecimal string can be copied and pasted from the output of ***lsblk -fm***

then

```
sudo ddrescue -f -n /dev/sda /dev/sdd "/media/ubuntu/and-a-string-of-hexadecimal-digits/logfile"
sudo ddrescue -d -f -r3 /dev/sda /dev/sdd "/media/ubuntu/and-a-string-of-hexadecimal-digits/logfile"
```

Notice that the system has automounted the partition with the UUID as the part of the mountpoint.

---

### Post by BrianV on 2016-10-26
See the screenprint for output of lsblk -fm

There is no mention of /media/ubuntu/ hex string for this internal hard drive. I can't see any mountpoint listed for sdb or sdb1, but there is a hex UUID for sdb1: CCFCD2BBFCD29F50. Should I use

sudo ddrescue -f -n /dev/sda /dev/sdd "/media/ubuntu/CCFCD2BBFCD29F50/logfile"
sudo ddrescue -d -f -r3 /dev/sda /dev/sdd "/media/ubuntu/CCFCD2BBFCD29F50/logfile"

Thank you!

---

### Post by sudodus on 2016-10-27
This is what I saw in a screenshot that you attached in post #14.

**CCFCD2BBFCD29F50** is the UUID hex string of /dev/sdb1, and it is also listed in the mountpoint column :-)

So I think your command lines are good now - just double-check that the drive letters still apply (have not been changed).

---

### Post by BrianV on 2016-10-27
More complications, probably because of running from a live USB.

When I enter the first command string, the response is:

sudo: ddrescue: command not found

Then, when I try to install gddrescue by:

sudo apt-get update
sudo apt-get install gddrescue

The response end with:

E: Unable to locate package gddrescue

Similar results trying to install Gimp and Gramps.

Do I need to do something different for the live USB to work? Or am I doing something else wrong?

---

### Post by BrianV on 2016-10-27
Reviewing the terminal output, after all the Gets in response to:    sudo apt-get update,   there are two lines:

** (appstreamcli:5163): CRITICAL **: Error while moving old database out of the way.
Appstream cache update failed.

This may be relevant.

---

### Post by sudodus on 2016-10-28
The package gddrescue is in the repository 'universe', that you add to your source list with the commands

```
sudo add-apt-repository universe
sudo apt-get update
```

That should make gimp and gramps available too.

---

### Post by sudodus on 2016-10-28
> **BrianV said:**
> Reviewing the terminal output, after all the Gets in response to:    sudo apt-get update,   there are two lines:

** (appstreamcli:5163): CRITICAL **: Error while moving old database out of the way.
Appstream cache update failed.

This may be relevant.

I think it works to install gddrescue, anyway, I suggest that you try,

```
sudo apt-get install gddrescue
```

Check the previous post: how to use the repository 'universe'. That is where you find gddrescue.

---

### Post by BrianV on 2016-10-28
[ATTACH=CONFIG]271818[/ATTACH][ATTACH=CONFIG]271819[/ATTACH][ATTACH=CONFIG]271820[/ATTACH]

I had success installing gddrescue with the live USB and started with the first command line. It appeared to be running fine, so I left it running. After an hour or so I came back to find the computer idle and unable to awaken. After re-starting on the live USB, I repeated the load universe, load gddrescue, run the command lines. Two of the screenprints show the terminal sequences and the logfile output.

After shutting the live USB down, I moved the Seagate drive to another computer (this one) and looked at the listed content, the third attachment. It seems to indicate the missing 40G is still missing.

What should my next step be?

---

Hope that description is clear enough. If not, just ask. Thank you.

---

### Post by sudodus on 2016-10-28
- Why did you interrupt the second run with ctrl C? It can be extremely slow, when it encounters some bad part of the disk. It tries and tries with small chunks of data ...

-How big is the disk (total size)?

I would let the second run continue until it finishes by itself.

---

### Post by BrianV on 2016-10-28
I didn't use ctrl C at any point.

On the last attempt, I issued the first command string and immediately got the response indicated. Then I issued the second command string and immediately got the result shown.

Is it that gddrescue examined the logfile and concluded the cloning was already completed?

---

### Post by BrianV on 2016-10-28
The hard drive is 80G, though gparted only listed the top 40G.

---

### Post by sudodus on 2016-10-28
If I understand correctly, your screenshot tells me 'rescued: 80026 MB', which means that ddrescue could clone all of it.

The reason why gparted does not see it is another problem, maybe some error in the partition table or file system, and you might be able to repair it with testdisk or some other tool. I suggest that we ***invite other people, who can help*** with ideas how to recover the file system or at least files.

My first suggestion is ***testdisk*** and if it does not work, ***photorec***. See this link [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

-o-

It is easier than screenshots (I think both for you and me) to copy text from the terminal window and paste it in a reply box 'here'. After that put it within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by BrianV on 2016-10-28
Thank you for the tutorial. My first attempt is the Analyze output from testdisk:

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdf - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 2 E extended              5307 215 27  9729  78 13   71030786
No partition is bootable
 5 L Linux                 5307 215 29  9541 199  2   68018176
   X extended              9541 199  3  9729  78 13    3012608
 6 L Linux Swap            9541 231 35  9729  78 13    3010560
```

At this stage the missing partition remains missing (Nothing below 5307 215 27)

---

### Post by sudodus on 2016-10-28
I think there are some options (more or less advanced algorithms) in testdisk, so there is still hope :-)

---

### Post by BrianV on 2016-10-28
This is the output after Quick Search. Rather a long while with 1TB to check!

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdf - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>* Linux                 5307 215 29  9541 199  2   68018176
 P Linux Swap            9541 231 35  9729  78 13    3010560










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large file Sparse superblock Recover, 34 GB / 32 GiB
```

So far, results look the same with the clone. But still no sign of the missing partition.

---

### Post by sudodus on 2016-10-29
Maybe you can try some even slower method with testdisk ...

---

### Post by BrianV on 2016-10-29
Seem to be running short of options. Here are the results of Deeper Scan:

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdf - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>  Linux                 5307 215 29  9541 199  2   68018176
   Linux                 7419 214 28 11653 198  1   68018176
   Linux                 7425  17 17 11659   0 53   68018176
   Linux Swap            9541 231 35  9729  78 13    3010560








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large file Sparse superblock Recover, 34 GB / 32 GiB

```

Not sure if there is anything more to try with testdisk, since the next screen says "No partition found or selected for recovery". Is there some way to use the knowledge that the missing partition is 40G and below 5307 215 29?

---

### Post by sudodus on 2016-10-29
I don't know.

Maybe you must resort to ***photorec*** in order to recover [some of] the files 'below 5307 215 29', that is from the lost partition.

Read the documentation at [http://www.cgsecurity.org](http://www.cgsecurity.org). You can select recovery of some single file type to avoid drowning in thousands of unsorted files. And continue with some other single file type.

---

### Post by BrianV on 2016-10-29
After reading stuff about the Partition Table, it seems it can be edited if it becomes corrupted. Is it possible to add a partition to the table, using addresses below the ones that have shown up? The End address would be  5307 215 29 - 1 (start of the first partition shown - 1), but what would the Start address be?

Is a trial like that worthwhile before trying ***photorec***?

---

### Post by sudodus on 2016-10-29
I don't know enough about file systems to reply to that question. I can only say maybe. I think it would be a very advanced task, and it might destroy things. On the other hand, it is only a cloned copy, so feel free to try!

---

### Post by BrianV on 2016-11-16
Well, sadly, I have had to resort to Photorec, which seems to have recovered my raw photos, without metadata. I have been able to restore more than half my photo collection from backup and will now begin the tedious process of extracting .jpg files from the 1200 recovered directories, checking the images against my backed up collection, and using memory (human) to assign the newly recovered ones. Wish there had been an easier way, but I'm grateful that the programs and adive were available to make this possible. Thank you for the patience and assistance.

---

### Post by sudodus on 2016-11-16
I'm glad that you can recover your important photos :-)

It could be both better and worse. Using Photorec means a lot of manual work, but it is often possible to save quite a lot of the total amount of 'lost' files.

-o-

Many of us have similar experiences, and it makes us take regular backups, and to recommend regular backups. Finally, don't forget to test that it really works to restore from the backup copy.

---

