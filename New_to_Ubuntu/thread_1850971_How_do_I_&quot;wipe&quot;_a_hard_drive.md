---
title: "How do I &quot;wipe&quot; a hard drive?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-09-27
Hello everyone,
I'm wondering how I would go about "wiping" a hard drive. I just sold my Mac on ebay, now I've got the hard drive hooked up to my Ubuntu laptop and I'm wondering how to wipe it before I ship it.

I know simply deleting the files is not enough. Is there a simple terminal command or something cool like that to overwrite all the data? 

Please help! Thanks!

---

### Post by collisionystm on 2011-09-27
Sledgehammer.

---

### Post by 2F4U on 2011-09-27
This article describes to methods, one for individual files and one for the whole hard drive:

[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)

---

### Post by jon zendatta on 2011-09-27
read this thread [http://ubuntuforums.org/showthread.php?t=778991]("http://ubuntuforums.org/showthread.php?t=778991")

---

### Post by collisionystm on 2011-09-27
Couldn't the program badblocks that comes with ubuntu wipe the drive? Theoretically it should. It writes Zeros to the entire drive trying to find bad sectors. This should wipe the drive clean.

---

### Post by Ranger_Joe on 2011-09-27
Here's what I ended up doing:

[http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-usb-hard-drive](http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-usb-hard-drive)

I just used the "shred" command to wipe the whole disk:

```
sudo shred -v /dev/sdb -z
```

Basically, this overwrites the hard drive 4 times with random data and rewrites it with all zeros afterwards. I think that should suffice.

---

### Post by Basher101 on 2011-09-27
since i dont mess with hard disk commands at all, the shred command looks more of a destructive command than cleaning :D

---

### Post by ddnev45 on 2011-09-27
[I've used Dban in the past.]("http://www.dban.org/")

---

### Post by cottfcfan on 2011-09-27
Kill Disk is the best method i've found.
Wipes the disk completely, but doesn't destroy it.
Ive used it twice on my current machine.
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by yetiman64 on 2011-09-27
> **Basher101 said:**
> since i dont mess with hard disk commands at all, the shred command looks more of a destructive command than cleaning :D

With shred, by default, there are 3 overwriting passes (for secure erasure of data) and the -z (zero) switch is the 4th pass in the OP's case. One single pass with zeros is much quicker/convenient if very secure erasure is not needed. shred and dd are no more destructive to a hard drive than any commercial software with a "nice" name (like dban), they all work the same way as far as I'm aware by doing overwriting passes on the drive.

OP I suspect you wanted secure erasure and what you did should work nicely, though if done to a whole disk, you will need to add back an msdos partition table using gparted (on the live cd if you don't have it in your install) before the drive can be reformatted and used again. 

**Edit:** just noted on rereading that this is on an old mac, the partition table will still need replacing, though I'm not sure what type a mac uses.

If you ever want to erase a drive you could use the "iterations=0" or "n 0" switch and the -z (zeroing) switch to reset every bit on the drive to a 0 without the 3 overwriting passes. This speeds up the erase time significantly but is less secure as far as forensic recovery is concerned (if that is a concern here, that is).

I tend to stick to the tools supplied on the Ubuntu install disc after some hardware incompatibility problems when trying to use dban a few years back (I believe it has improved of recent, though I don't use it anymore.)

---

### Post by Paqman on 2011-09-27
> **Ranger_Joe said:**
> 
Basically, this overwrites the hard drive 4 times with random data and rewrites it with all zeros afterwards. I think that should suffice.

Actually shred's default is _25_ writes, plus your zero making 26, which is a bit ridiculous. A single pass is enough, and would be done a lot, lot quicker. Doing multiple wipes on drives the size of what most people have now is excruciatingly slow, and completely unnecessary.

Shred is designed to wipe files anyway. If you want to wipe free space you can use the tool sfill, which comes in the same [secure-delete](apt:secure-delete) package as shred.

So to wipe your empty drive:
```
sudo sfill -l -l -v -z /mount/point
```
This would do a single pass with zeros across the whole drive. Dropping the -z would use random data instead.

---

### Post by Ranger_Joe on 2011-09-27
> -z (zero) switch is the 4th pass*Sorry. I should have said that the command I found will write random data THREE times, not four. The zeros ARE the fourth pass. Sorry.

Thanks for the correction!

---

### Post by Ranger_Joe on 2011-09-27
>  just noted on rereading that this is on an old mac, the  partition table will still need replacing, though I'm not sure what type  a mac uses.Yetiman64,
This would be a task for the new owner to perform right? I'm selling this Mac for scrap parts as it is broken. Is it fair to assume that if the new owner wants to use the drive, they can set up a partition table themselves?

---

### Post by yetiman64 on 2011-09-27
> **Paqman said:**
> Actually shred's default is **_25_** writes, plus your zero making 26, which is a bit ridiculous. A single pass is enough, and would be done a lot, lot quicker. Doing multiple wipes on drives the size of what most people have now is excruciatingly slow, and completely unnecessary.

Shred is designed to wipe files anyway. If you want to wipe free space you can use the tool sfill, which comes in the same [secure-delete]("apt:secure-delete") package as shred.

So to wipe your empty drive:
```
sudo sfill -l -l -v -z /mount/point
```This would do a single pass with zeros across the whole drive. Dropping the -z would use random data instead.
Check out man shred on a release Lucid or later and you will see it is 3 passes, the ridiculous 25 passes of earlier versions has been changed.


> -n, --iterations=N
              overwrite N times instead of the default (3)**Edit: **
> **Ranger_Joe said:**
> Yetiman64,
 This would be a task for the new owner to perform right? I'm selling  this Mac for scrap parts as it is broken. Is it fair to assume that if  the new owner wants to use the drive, they can set up a partition table  themselves?
 Takes only a few seconds to do with gparted off a live cd either by yourself or the new owner, it is not a major block if you know what is stopping the use of the drive (maybe if you left it as is and included a note the drive has been erased and needs a new partition table may help IF the new owner uses the hard drive).

---

### Post by Paqman on 2011-09-27
> **Ranger_Joe said:**
> Yetiman64,
This would be a task for the new owner to perform right? I'm selling this Mac for scrap parts as it is broken. Is it fair to assume that if the new owner wants to use the drive, they can set up a partition table themselves?

I always make sure drives are formatted with something usable before selling them. If not, probably best to be explicit in your ad about what they'll be getting.

---

### Post by Paqman on 2011-09-27
> **yetiman64 said:**
> Check out man shred on a release Lucid or later and you will see it is 3 passes, the ridiculous 25 passes of earlier versions has been changed.

Ah, that's good. Three is still overkill IMO. There's no reason to do any more than one. Nobody is going to be taking an electron microscope to your platters, and one pass will defeat any software tool.

---

### Post by yetiman64 on 2011-09-27
> **Paqman said:**
> Ah, that's good. Three is still overkill IMO. There's no reason to do any more than one. Nobody is going to be taking an electron microscope to your platters, and one pass will defeat any software tool.

Agree totally, that is why when I use shred I use,

```
sudo shred --force --iterations=0 --verbose --zero /dev/sd**XY**
```I use only /dev/sdX to wipe a complete drive and /dev/sdXY to wipe a specific partition on a drive. No overwriting (for forensic level worries etc) just zeroing before reusing/resetting up a partition or drive with a new system, though the switch -n does allow for random data overwriting (if needed).

---

### Post by Ranger_Joe on 2011-09-27
> I always make sure drives are formatted with something usable before  selling them. If not, probably best to be explicit in your ad about what  they'll be getting.

Paqman, can I just use gparted to do that?

---

### Post by wolfen69 on 2011-09-27
> **Ranger_Joe said:**
> Paqman, can I just use gparted to do that?

Personally, yes, I would just delete the partition using gparted and be done with it. I highly doubt anyone is going to use specialized software to get at your files. But if you really feel you must securely delete, one pass will be good enough.

---

### Post by Slim Odds on 2011-09-27
> **wolfen69 said:**
> Personally, yes, I would just delete the partition using gparted and be done with it. I highly doubt anyone is going to use specialized software to get at your files. But if you really feel you must securely delete, one pass will be good enough.

Deleting the partition is super simple to RESTORE. It's not what you want to do if you don't want someone getting your old data.

---

### Post by Paqman on 2011-09-27
> **Ranger_Joe said:**
> Paqman, can I just use gparted to do that?

For quickly formatting it? Sure.

---

### Post by wolfen69 on 2011-09-27
> **Slim Odds said:**
> Deleting the partition is super simple to RESTORE. It's not what you want to do if you don't want someone getting your old data.

I should add that after a partition is deleted, I always reinstall an OS before giving it to someone. Not worried.

---

### Post by srs5694 on 2011-09-27
> **wolfen69 said:**
> [quote=Ranger_Joe]Paqman, can I just use gparted to do that?Personally, yes, I would just delete the partition using gparted and be done with it. I highly doubt anyone is going to use specialized software to get at your files. But if you really feel you must securely delete, one pass will be good enough.[/QUOTE]

My interpretation is that Ranger_Joe has already decided to use shred on the disk, and only wants to create a partition table as a courtesy to the new owner. If so, GParted can do the job, although since the computer is being sold for parts, leaving it completely unpartitioned is perfectly reasonable. In fact, partitioning a "for-parts" disk may be inadvisable, since there are at least three types of partition tables that a new owner might want to create on it (APM, MBR, and GPT), and if you create the wrong type it might actually become harder for the new owner to properly create the right type. In particular, some tools don't completely wipe GPT or APM data when converting to MBR, which can lead to some programs getting confused and showing incorrect partition data.

If you do want to create a new partition table, I recommend creating the native type for the machine. For an older (PowerPC or 680x0) Mac, this would be APM. For a newer (Intel-based) Mac, it would be GPT. When using GParted, you've got to click the "Advanced" item in the dialog box when creating a partition table to be able to select the type; if you don't do this, it'll create an MBR partition table.

---

