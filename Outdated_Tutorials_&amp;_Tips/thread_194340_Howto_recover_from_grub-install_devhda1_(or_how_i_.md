---
title: "Howto recover from grub-install /dev/hda1 (or how i got XP back)"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Amon_Re on 2006-06-11
This might be a very usefull howto for those who have dual booting systems, and have overwritten their NTFS (or vFat) bootblock with grub.

**The problem:**
You just edited your menu.lst file, and wrote grub to the wrong place, overwriting the boot sector of your windows partition.

You reboot and wich to boot windows, only to find it no longer boots, and even worse, you can't mount your ntfs partition anymore.

when you try to manually mount the partition you get an errror, prompting you to look at dmesg output.

You look, and you get this:
```
[4295568.716000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4295568.716000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4295568.716000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS vol ume.
```

If this is your situation, then don't panic!

**The solution:**
First you should try to mount the partition like this:
sudo mount -t ntfs -o errors=recover /dev/hda1 /mnt/test
If this works, backup your most important stuff first! (Yes, you should always have backups!)

Now comes the cool part, download and install TestDisk ([http://www.cgsecurity.org/wiki/TestDisk):](http://www.cgsecurity.org/wiki/TestDisk):)
sudo apt-get install testdisk

After installing it, start it:
sudo /usr/sbin/testdisk

Then highlight the disk you need, and go to [mbr code]
In this screen you can replace the mbr with the backup mbr, and this should solve the problem of windows not booting.

PS: This should work with ubuntu, kubuntu & whatnot.

---

### Post by AkumA on 2007-02-07
I've made the same mistake and i've posted about it!
After 1 day and half of digging internet i've found it here!

I'll try right now.. i hope it works, i've tried many methods and i've installed and erased grub many times.. i hope it works anyway :(

---

### Post by AkumA on 2007-02-07
Done.. in the next boot i've found

```
1234E:
```

Or if it wasn't "E" at the end it was another letter.. hexadecimal i suppose.

I've reinstalled grub and i get on my Ubuntu Again, but the windows partition still is "???" on GParted.
I'll try to make it again and see what happends with windows installer. :)

---

### Post by AkumA on 2007-02-08
I've tried lot of things but nothing, i've formatted.
By the way, there where other guides that mabe could help fix (Ubuntu Official Guides -> Super Grub Disk)

I just want to tell another thing that happened to me.
After the winxp installation CD boot i've seen the partition "Lost". I've formatted it as NTFS (Fast format) and i've installed WinXp.
When i got back WinXp up and running (Brand new.. wow.. it's fast :D!) i've installed grub (Boot Edgy Ubuntu cd -> fix broken system -> reinstall grub)i was unable to see the other Disk on my pc, a 160Gb divided like this:
```
 /hdb1/ ntfs data (From internet, isos, bla bla)
/hdb2/ Slackware Root File System (ReiserFS)
/hdb3/ Home for Both Linux Ubuntu & Slackware (ReiserFS)
/hdb4/ swap

```

Partition Magic could not fix it, Ubuntu Dapper Live CD could not see and so on.
I used testdisk
```
sudo apt-get install testdisk
```

With both test disk and cfdisk the partition was "Fat16" bla bla
Launchin' on TESTDISK the "Analyze" command after a secondo he showed me what i wanna see! My disk like it is!
I've wrotten the changes.. and here i am, after rebooting, on my Ubuntu Edgy XGLed on a GeForce2 :D

yeah! :guitar:

---

### Post by theToolman on 2007-02-09
Thanks, testdisk is exactly the right tool I was looking for.

I also had a very similar problem; 

 i accidentally  put grub onto the windows partition instead of the MBR.  That partition just wouldnt boot until I found this thread.

I booted a windows recovery console (on install disk) and used the "fixmbr"  and  "fixboot" commands, but it still wouldnt boot Windows. Those are still nessecary steps I beleive, but the final piece of the puzzle is to repair the orginial boot sector with the backup - i noted that when my ubuntu boots and mounts the vfat partition it warned that the bootsector was mismatched to its backup.  

[http://savannah.gnu.org/bugs/?17472](http://savannah.gnu.org/bugs/?17472)

this post menstions copying the boot sector by hand without an example :(  so I was considering using dd something like this 

[http://forums.devshed.com/linux-help-33/manually-backup-boot-sector-405731.html](http://forums.devshed.com/linux-help-33/manually-backup-boot-sector-405731.html)

but even that is only half the answer - thats a backup to file.

testdisk does it with a text gui - very easy :)  free software and the static binaries worked fine for me on the livecd to repair my xp partition.  I copied THE BACKUP over the original within the tool.

---

### Post by adrian15 on 2008-04-29
> **Amon_Re said:**
> This might be a very usefull howto for those who have dual booting systems, and have overwritten their NTFS (or vFat) bootblock with grub.

**The problem:**
You just edited your menu.lst file, and wrote grub to the wrong place, overwriting the boot sector of your windows partition.

You reboot and wich to boot windows, only to find it no longer boots, and even worse, you can't mount your ntfs partition anymore.

when you try to manually mount the partition you get an errror, prompting you to look at dmesg output.

You look, and you get this:
```
[4295568.716000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4295568.716000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4295568.716000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS vol ume.
```

If this is your situation, then don't panic!

**The solution:**
First you should try to mount the partition like this:
sudo mount -t ntfs -o errors=recover /dev/hda1 /mnt/test
If this works, backup your most important stuff first! (Yes, you should always have backups!)


This recover errors mount error might not work. Isn't it ?

adrian15

---

### Post by adrian15 on 2008-04-29
> **Amon_Re said:**
> 
Now comes the cool part, download and install TestDisk ([http://www.cgsecurity.org/wiki/TestDisk):](http://www.cgsecurity.org/wiki/TestDisk):)
sudo apt-get install testdisk

After installing it, start it:
sudo /usr/sbin/testdisk

Then highlight the disk you need, and go to [mbr code]
In this screen you can replace the mbr with the backup mbr, and this should solve the problem of windows not booting.

PS: This should work with ubuntu, kubuntu & whatnot.

This [mbr code] does not fix the partition boot record, isn't it? It only fixes the mbr boot code, isn't it?

adrian15

---

### Post by adrian15 on 2008-04-29
> **theToolman said:**
>  accidentally  put grub onto the windows partition instead of the MBR.  That partition just wouldnt boot until I found this thread.

testdisk does it with a text gui - very easy :)  free software and the static binaries worked fine for me on the livecd to repair my xp partition.  I copied THE BACKUP over the original within the tool.

testdisk does restore the partition boot record with the 6th sector partition boot backup? That's what you mean? Or do you mean that you make a backup to a file and you restore it?

adrian15

---

### Post by adrian15 on 2008-04-29
> **theToolman said:**
> 
[http://savannah.gnu.org/bugs/?17472](http://savannah.gnu.org/bugs/?17472)

this post menstions copying the boot sector by hand without an example :(  so I was considering using dd something like this 


My bet is:

```

dd if=/dev/hda1 of=/path/to/my_backup_file.bin count=1 bs=512 skip=6
dd if=/path/to/my_backup_file.bin of=/dev/hda1 count=1 bs=512

```

**If anyone has some qemu windows images with these problems and want to try my solution to see if I am right or wrong... please try it.**

Note that you will also need to run fixmbr, fixboot and maybe bootcfg /rebuild.

adrian15

---

### Post by Rich P on 2010-04-28
I followed the instructions in the original post and want to add some clarification. If you have a dual boot system with the Windows NTFS partition on hda1 and you issued the command "grub-install /dev/hda1", you need to follow different directions than above to fix the boot sector on hda1. After starting testdisk, choose the "Advanced" option instead of "MBR". Then select the partition that has the hosed boot sector (in this case hda1), next select "Boot" for Boot sector recovery and finally select "Copy backup" to copy your backup boot sector into place. This worked for me. Thanks!  --RP

---

