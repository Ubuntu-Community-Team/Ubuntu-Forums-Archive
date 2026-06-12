---
title: "files disappeared from external hard drive: empty folders present, space occupied"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by neouser on 2011-09-18
While window with list of folders from external hard drive was open on my desktop, the cable of external hard drive was disconnected.
 
After that, all files (different types) disappeared from my external hard drive. The folders are still listed but empty. The total space is still used for external drive but properties of single folders show no space usage. Folders show the time and date of disconnection as date for "last modification". I tried to look in trash, to look for or display "hidden files", but nothing.
 
In case it may matter:
External hard drive is from Toshiba and about three years old
Laptop: Dell mini 9 with Ubuntu 10.4
 
Does anyone have suggestions on what to do?
 
Thanks!

---

### Post by IHeequ5i on 2011-09-18
I admit that I haven't used an external hard-drive since Iomega's ZIP drives were common, so I may be talking through my hat here.  With that disclaimer:

Close all windows and applications that use the hard-drive, then power down the hard-drive and restart it.

---

### Post by Lisiano on 2011-09-18
Interesting. Try running these commands
```
mount
```
```
df -h
```
```
cd /media/Name-Of-Your-Hard-Drive
ls -lha
ls -lha *
```

---

### Post by neouser on 2011-09-18
Maybe I do not understand your suggestion.
 
From my understanding the hard drive cannot be powered down. It is only connected with a USB slot and can merely be "ejected" or "savely removed". Just like a USB flash memory-stick.

---

### Post by Lisiano on 2011-09-18
Powering down means disconnecting it from any power source or actually telling the device to "Shutdown" or "Halt", so in your case it means disconnect it from the PC and any external power if it's a HDD

---

### Post by neouser on 2011-09-18
> **Lisiano said:**
> Interesting. Try running these commands
```
mount
```
```
df -h
```
```
cd /media/Name-Of-Your-Hard-Drive
ls -lha
ls -lha *
```
 
 
Hi, I tried to use the listed commands. In-between a list of files (or folders) appeared in my terminal but after closing the terminal the problem does not seem to be solved. Still only folders, no files.

---

### Post by neouser on 2011-09-18
> **Lisiano said:**
> Powering down means disconnecting it from any power source or actually telling the device to "Shutdown" or "Halt", so in your case it means disconnect it from the PC and any external power if it's a HDD
 
Ok, that is clear. I properly disconnected the HDD several times, but no change. I also tried to do this on another computer with windows xp: same issue.

---

### Post by vanadium on 2011-09-18
If the drive was disconnected at a crucial moment, the file system might have been damaged. I guess that the drive was formatted with the FAT32 file system. that is the only file system for which I would estimate that it could be completely destroyed after having been closed unproperly. More modern systems such as ext, or ntfs, are more resilient to damage from a power outage.

You may check the file system using fsck. fsck does automatically recognize the file system. If it doesn't (anymore), then that is a bad sign.

- determine the device name of your USB drive (something like /dev/sd??, e.g. /dev/sdc1) from the output of
```

sudo blkid

```
- Let us assume it is for example /dev/sdc1. Unmount the partition
```

sudo umount /dev/sdc1

```
and check the file system
```

sudo fsck /dev/sdc1

```
The command will repair in case of ext or ntfs. In case of fat, you will get a report status. For repair, the option -a or -r (see "man dosfsck") is needed to actually commit a repair. However, in the latter case, a repair will make the file system consistent, but many files may be corrupt, containing the wrong data.

---

### Post by Lisiano on 2011-09-18
I should have been more clear, I wanted you to also post the output of those commands here. But yes, if you only saw a list of folders (Those are in blue) then it is likely a corrupted filesystem as vanadium said.

---

### Post by neouser on 2011-09-18
> **vanadium said:**
> If the drive was disconnected at a crucial moment, the file system might have been damaged. I guess that the drive was formatted with the FAT32 file system. that is the only file system for which I would estimate that it could be completely destroyed after having been closed unproperly. More modern systems such as ext, or ntfs, are more resilient to damage from a power outage.
 
You may check the file system using fsck. fsck does automatically recognize the file system. If it doesn't (anymore), then that is a bad sign.
 
- determine the device name of your USB drive (something like /dev/sd??, e.g. /dev/sdc1) from the output of
```

sudo blkid

```
- Let us assume it is for example /dev/sdc1. Unmount the partition
```

sudo umount /dev/sdc1

```
and check the file system
```

sudo fsck /dev/sdc1

```
The command will repair in case of ext or ntfs. In case of fat, you will get a report status. For repair, the option -a or -r (see "man dosfsck") is needed to actually commit a repair. However, in the latter case, a repair will make the file system consistent, but many files may be corrupt, containing the wrong data.
 
The code "sudo blkid" shows me 3 lines: /dev/sda1, /dev/sda5, and /dev/sdb1. The latter one: "/dev/sdb1: LABEL="USB-HDD" UUID="281A-0DE9" TYPE="vfat"" So I thought this is the one.
 
The command "sudo unmount /dev/sdb1" cannot be found

---

### Post by ajgreeny on 2011-09-18
> **neouser said:**
> The command "sudo unmount /dev/sdb1" cannot be found
It should be "sudo [COLOR=Red]umount[/COLOR] /dev/sdb1" not "[COLOR=Red]unmount[/COLOR]".  Note no N in umount.

---

### Post by neouser on 2011-09-18
The command: "sudo fsck /dev/sdb1" seemed to work. Now I have a list with tthe folders followed by "Start does point to root directory. Deleting dir."
 
It finishes by saying: 
*Reclaimed 87655457 unused clusters (297765443344.. bytes). *
*Free cluster summary wrong (587665 vs. really 9560941)*
*1) correct*
*2) don't correct*
*?*
 
Which option should I choose?

---

### Post by Lisiano on 2011-09-18
Once you press 1) Correct. You get 270+gigs free. Once you pres 2) Don't correct. You get nothing.
In short, you lost your files, but there is a way to recover what is left of them.
You have to learn what partition table it is using, go to System -> Administration -> Disk Utility and find your external HDD, note what it says under Partitioning (If Master Boot Record then it's Intel)
Install a program called TestDisk and PhotoRec
```
sudo apt-get install testdisk
```
Now you will have to restore the files using photorec, well, what is left of them.
```
sudo photorec /dev/sdb
```
Proceed -> Intel -> Pick the 1st partition -> Pick whatever FS it is (Usually FAT, also check using Disk Utility), Free (Or Whole if you did not select to reclaim the 270+ gigs free) then find a directory you will save the files (Somewhere NOT on your external HDD, another external HDD or your Internal HDD), if you don't have enough space, it will fill it up then ask you to select a new place to save the files. Once you find a good place, press Y.

---

### Post by neouser on 2011-09-18
That is not the news I was hoping for...
 
I will give it a try. I'll first need to find a new storage place...

---

### Post by Lisiano on 2011-09-18
Well, sorry for your loss, I guess. Also I can't stress enough how you MUST NOT WRITE ANYTHING to your external HDD. If you do so, some or all files will be overwritten, until then label it as a "Do NOT use under ANY circumstances" or something.

---

### Post by vanadium on 2011-09-18
This is indeed a fat drive, as shown by the output of your blkid command. Unfortunately, while the data is still on your disk, the "housekeeping" data are lost.

Use vfat only for USB sticks where only little and temporary data is stored. For storage media, use modern, more resilient file systems such as ext3 or ext4 on linux.

Unfortunatelly, you indeed have a problem if you do not have a backup of these data. Trying to rescue some is your only bet, and there, I second the hint of Lisiano to attempt photorec.

Maybe unnecessary to say, but you always need a backup of data for which you care. Now, it was an accidental disconnection at the wrong moment, but also hardware failure may at any time threaten your data. So even with a better file system, you still need the backup.

---

### Post by bubeck on 2011-09-18
> **vanadium said:**
> 
...
Use vfat only for USB sticks where only little and temporary data is stored. For storage media, use modern, more resilient file systems such as ext3 or ext4 on linux.
...


I completely agree with vanadium, but needless to say, you will not be able to access the contents of this drive from Windows without going to the trouble of installing software on Windows.  Or on a Mac for that matter.

There's no happy middle ground unfortunately.

---

### Post by staticd on 2011-09-18
ntfs?

---

### Post by Lisiano on 2011-09-18
Since when Linux has native NTFS support?

---

### Post by SeijiSensei on 2011-09-18
> **Lisiano said:**
> Since when Linux has native NTFS support?

Solid read/write support came with [ntfs-3g]("http://en.wikipedia.org/wiki/NTFS-3G") about three years ago.  The previous ntfs driver was read-only.

@OP
If, as we suspect, the external drive has a DOS or NTFS filesystem, you really need to connect the drive to a Windows machine and run "chkdsk" against it.  While the ntfsfix program that comes the [ntfsprogs]("http://www.tuxera.com/community/ntfs-3g-download/") suite can fix some problems, I really only trust Microsoft's utilities with a broken NTFS filesystem.

---

### Post by Lisiano on 2011-09-18
> **SeijiSensei said:**
> If, as we suspect, the external drive has a DOS or NTFS filesystem, you really need to connect the drive to a Windows machine and run "chkdsk" against it.  While the ntfsfix program that comes the [ntfsprogs]("http://www.tuxera.com/community/ntfs-3g-download/") suite can fix some problems, I really only trust Microsoft's utilities with a broken NTFS filesystem.
By native I meant full support. Thus using NTFS also implies you have a nearby Windows system on which you can check the drive for errors. Which is not cool when you try to be Windows-independent. Thus the only viable solution for external memory is FAT. Also DOS does not support NTFS without manually adding drivers for it (By default that is).
Now for people that don't want Windows PC's to see their drives (Me), they can use *Nix filesystems like EXT but then Windows will see it as unformatted... And probably format it or some user will. Again, only FAT is viable.
So personally I would choose EXT4 but due to compability... I have to say, FAT and Safe Ejection.

---

### Post by neouser on 2011-09-23
Hi,

I'm back. 
It took some time but I was able to recover some of the files (about 1/3). I had backup of most of the data, but did not yet have the time to backup some important pictures. I'm happy I managed to recover some. THANKS FOR YOUR ASSISTANCE!

Now I have a **new problem**:
In order to save the recovered data I bought a new external hard drive. When I try to unmount it, my screen is blocked. Sometimes just the arrow, sometimes it just becomes black. I tried to reformat the hard drive, but nothing changed. This problem now happens with both: the new hard drive and the old hard drive.

---

### Post by neouser on 2011-09-24
> **neouser said:**
> Hi,

I'm back. 
It took some time but I was able to recover some of the files (about 1/3). I had backup of most of the data, but did not yet have the time to backup some important pictures. I'm happy I managed to recover some. THANKS FOR YOUR ASSISTANCE!

Now I have a **new problem**:
In order to save the recovered data I bought a new external hard drive. When I try to unmount it, my screen is blocked. Sometimes just the arrow, sometimes it just becomes black. I tried to reformat the hard drive, but nothing changed. This problem now happens with both: the new hard drive and the old hard drive.


Since most of the files were recovered and the original problem was (partly) solved, the above mentioned new problem is posted in a new thread: [http://ubuntuforums.org/showthread.php?t=1849361](http://ubuntuforums.org/showthread.php?t=1849361)

---

