---
title: "Ubuntu/winxp Installing Problem"
date: 2007-07-31
forum: Other OS Talk
---

### Post by Kohak on 2007-07-31
OK let begin with the setting I had before I did the problems.

1 hardrive of 200gb on it 4 partitions:

1 - Win32Xp (50gb)
2 - Ubuntu (10gb)
3 - Data backup (126gb)
4 - Swap (500mb)
Rest Free Space
-----------------------------------------
The Story:
Yesterday I decide to have 3 Os, I do web designing and I like it to have 3 OS with many browser to do the testing. The 3 OS were Ubuntu, Win32Xp, and Tiger. So first I need it space for the Tiger Os. So i Format my Window and reinstall it with 40 gb, to leave 10gb for my Tiger OS,

The step I manage to do well were:
1 - Format Window Partition
2 - Make a new partition of 40gb
3 - Install/copy the component.
4 - Get to the restart part.

After Restart, I will let window not boot from the cd, and let it keep going to the second part, but I never comes, it get stuck in the Question if I want to "boot from Cd Press any key".

--------------------------

So I delete all my partition except for my Backup one, because I thought my Swap was making the problem, plus my Ubuntu was really new, so I didn't worry about the setting and stuff I install on it. The new Setting is:

1 - free space of 60 gb
2 - Backup Partition (126 gb)
3 - Rest of Free Space

But the the same problem of win32xp still going on, I don't think it a hardware problem, because I can install Ubuntu.

Thanks in advance,

Edit: I forget to point out that now if I try to install Window it will be install on the D: since My backup end up been in my C:.

---

### Post by smoker on 2007-08-01
hi, a couple of suggestions,

after restart, the pc is stalling, presumably because it is not finding the boot sector in your new install, a new install should automatically rename the windows partition as 'C', and rename other partitions it can see, so, eg, your backup partition may be now 'D' or 'E', whatever (as long as it is fat or ntfs!).

first, if your windows partition is not the first partition on the drive, i would use gparted, or other partitioning app, to move your data partition to make room at the start of the drive for the xp install.

if this is already the case, check the drive is showing ok in the bios, ie, primary master, or if a sata, did you install sata drivers during install?

disable any other possible boot options that may be confusing the system, eg, floppy boot, network, usb boot, etc, leaving just the options cd-rom first, then first hard drive second.

if you have any other hardware attached to the computer, disconnect during install, leaving just the keyboard, mouse, monitor connected. especially make sure any card reader is disconnected (if you have an internal card reader, open the box and disconnect the cable to disable it).

if none of the above works, clean the cd and cd-rom, the install cd may be dirty or faulty - you could maybe try this first!

if you have, or can, backup your data patition and restore the drive to one large partition and use the hard drive manufacturers app (free from their support page) to do the equivalent of a 'low-level format'

it is always wise to have backups of crucial data especially when partitioning drives!

best of luck.

---

### Post by mips on 2007-08-01
How many primary partitions do you have ? The limit is 4 so if you exceed it you need to look at extended/logical partitions.

---

### Post by Kohak on 2007-08-01
Hey thanks for the tips. 

I have a couple of question, 

How do I rename the Letters I try googling but I can't find anything and it have to be something that ubuntu support since it the only OS I can run.

Also for some reason when I make the partition for window, it will leave a litle free space on top of it, this can also make the problem,

Now I'm thinking of getting a new Hard Drive, using this one for backup and the new one for the OS.

anyways, I want to see if I can fix before, I will give you more details after I do some tries

thanks.

Mips: I have 2 partitions one is the Backup and the other one will be windows. So even if both are primary, I still have 2 more primary space left, also if you know how to set a exteded/logical to primary, I will like to know, Thanks also.

---

### Post by smoker on 2007-08-02
> **Kohak said:**
> How do I rename the Letters I try googling but I can't find anything and it have to be something that ubuntu support since it the only OS I can run.

Also for some reason when I make the partition for window, it will leave a litle free space on top of it, this can also make the problem,

hi, if you mean your drive letters, eg, 'C', 'D', etc, you can only change these within a windows install, using computer management, in xp. linux uses a different naming convention for drive partitions, eg, 'hda1, hada2' or 'sda1, sda2', or a variation of such. once you install xp, xp will then name your partitions, and you can then change to suit.

if this 'little free space' is at the start of the drive, that is probably why the bios cannot find the boot sector in your xp install. the bios will look here for the boot files, and if it cannot find them, or find directions to where they are, then it will stall.

if you can download the 'gparted live-cd' and use that to set your partitions making sure that your windows partition is at the start of the drive, you can download the bootable live-cd from here:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

as far as primary and logical partitions go, you can set these through gparted also. i believe xp will only install on to a primary partition.

as always, make backups of crucial data before partitioning drives,

best of luck

---

