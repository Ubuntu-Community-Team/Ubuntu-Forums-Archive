---
title: "Invisible files on sd card"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by t0p on 2008-10-21
I'm running ubuntu on an Eeepc.  I keep a 4GB sd card in the Eeepc.  Up til now it's been okay.  But now, the netbook doesn't want to boot if the sd card is plugged into it.  If I put the card in its slot, it will automount... but it's "blank", if I go to Places I can see there are no files on the card. They have vanished!

I know the files haven't really vanished.  They are still on the card - nautilus says there's 1 GB of empty space on the card, which means the card has shrunk; it should have 4GB of space.  So, there are 3GB of files on the sd card, but the Eeepc can't see them.  How can I make them visible again?  (Please note, **View > Show hidden files** does not make them visible. These files are not regular hidden files).

Anyone know how I can get the files to show themselves?

---

### Post by kartoshka on 2008-10-21
Could be the filesystem is corrupt. Try running:

```
fsck *device*
```

to repair it.

---

### Post by gutsy08 on 2008-10-21
Do the files show up if you open a terminal window and do a "ls -la" in that directory?

---

### Post by sarah.fauzia on 2008-10-22
> **gutsy08 said:**
> Do the files show up if you open a terminal window and do a "ls -la" in that directory?

I am having the exact same problem (I also have Vista on this machine; I installed Ubuntu 8.04.1 with Wubi on my Lenovo X61T), and running ls -la _showed all of my files_. But if I go to the disk with Nautilus, it appears empty (but isn't in Vista). I would appreciate the help--thanks!

Note: When I originally installed Ubuntu with Wubi (only last night) I could read my files and write to the directories...but if I tried to delete a file, then my files would seem to disappear, but then would come back again. It was only after I unmounted my SD card with Ubuntu that it refused to work at all. I tried unmounting it with Vista and re-mounting with Ubuntu but that didn't work...

---

### Post by sarah.fauzia on 2008-10-22
> **kartoshka said:**
> Could be the filesystem is corrupt. Try running:

```
fsck *device*
```

to repair it.

```
fsck /media/disk
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /media/disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I tried that... did I not correctly enter the directory? I tried cd /media, then the command, and it tells me:

```
/media$ fsck disk
fsck 1.40.8 (13-Mar-2008)
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
```

I'm still not sure if it is reading the right disk, and I'm not quite sure of which option to pick... Again, thank you for offering your help! Unlike the original poster, however, I can boot with the SD card in the internal slot, I just have the problem I specified in my previous post.

---

### Post by Orange_and_Green on 2008-10-22
Hello :)

[EDIT]Sarmacid is right... Thank you for pointing out my mistake

Please unmount the sd card first by typing

```
sudo umount /media/disk
```

then run the fsck utility as superuser:

```
**sudo** fsck /dev/DEVICE_NAME
```

Where DEVICE_NAME is something like sdb1. Like Sarmacid said, the mount command will tell you (run it before you unmount)

Good luck :KS

---

### Post by Sarmacid on 2008-10-22
> **sarah.fauzia said:**
> ```
fsck /media/disk
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /media/disk
```

/media/disk is not the device, it's the location where the device is mounted. To find out the device, run

```
sudo mount
```

and you should see the device mounted in that directory. It should say something like /dev/sdb1

---

### Post by sarah.fauzia on 2008-10-22
Oh dear, the folder I had tried to write to on my SD card in Ubuntu became entirely corrupted. I lost some valuable data--not too much, since I keep backups... Any clue about that? I couldn't even delete the folder until I let Windows clean it up.

---

### Post by sarah.fauzia on 2008-10-22
Now to add to the mysterious--I can see the files on my SD card now, after having done the cleanup in Windows. I'm just very worried about trying to save files to it again, after the initial disaster, but I'll give it a shot.

---

### Post by sarah.fauzia on 2008-10-22
> **Sarmacid said:**
> /media/disk is not the device, it's the location where the device is mounted. To find out the device, run

```
sudo mount
```

and you should see the device mounted in that directory. It should say something like /dev/sdb1

Thanks, I did what you said to find the location and ran fsck:

```
fsck /dev/mmcblk0p1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/mmcblk0p1: 1401 files, 53485/490192 clusters

```

Did that just read my files, or did it fix anything? Again, I really appreciate the help, and I do hope the original poster finds a solution to this problem, too.

---

### Post by t0p on 2008-10-22
Hi, this is the OP, back again and I still need help!
Okay, first here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c0c8253c-ec64-49e1-86a8-d844c7628449 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=51dde39a-71e4-4607-bacc-877963971657 none            swap    sw              0       0
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0

```

The sd card in question is /dev/sdb1, or /media/MMCSD.

If I try to turn on the computer with the sd card in the card slot, the Eee pc won't boot,

After the computer has booted, I insert the card.  No icon appears as it used to.  And the card does not appear in **Places**.  But if I go to /media, I can see the card there: **/media/MMCSD**.  And I can save stuff on the card.  So it must be mounted, right?

Well, ubuntu certainly doesn't think so.  If I give the command

```
mount /dev/sdb1
```

I get this response:

```
mount: special device /dev/sdb1 does not exist
```

and the same happens if I try to mount /media/MMCSD.

I thought maybe I should just reformat the thing.  But **parted** and **gparted** both cannot see the card.  So formatting it is not possible.

There's also the fact that a load of files have disappeared from the card.

I tried:

```
t0p@engine:~$ sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

I don't understand that stuff above about e2fsck.

---

### Post by sarah.fauzia on 2008-10-22
> **Orange_and_Green said:**
> Hello :)

[EDIT]Sarmacid is right... Thank you for pointing out my mistake

Please unmount the sd card first by typing

```
sudo umount /media/disk
```

then run the fsck utility as superuser:

```
**sudo** fsck /dev/DEVICE_NAME
```

Where DEVICE_NAME is something like sdb1. Like Sarmacid said, the mount command will tell you (run it before you unmount)

Good luck :KS

Thanks! I followed this to the letter and got:

```
sudo fsck /dev/mmcblk0p1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/mmcblk0p1: 1401 files, 53485/490192 clusters

```

Is that what it was supposed to do? I'm going to try once again to delete a file...it's when I try deleting files that things seem to go haywire. Again, thanks for the help, and I again reaffirm that I hope OP also finds a solution! :)

[edit] No, deleting files still seems to bring on the vanishing act of my files. Goodness! And this isn't an old SD card--I bought it this year, and it worked perfectly fine on a Ubuntu install on another tablet. *confused* [/edit]

OP, do you have any similarities to my problem?

[edit]I tried running the fsck utility after the problem begins again and I get a different result:

```
sudo fsck /dev/mmcblk0p1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/mmcblk0p1
Could this be a zero-length partition?

``` [/edit]

---

### Post by t0p on 2008-10-22
> **sarah.fauzia said:**
> 
OP, do you have any similarities to my problem?
]

There are a few similarities: both of our sd cards are fairly new, we're both suffering from corrupted filesystems on the cards... but that's about it.

I guess I'm gonna have to work out that **e2fsck** command (which I've ner come across before).  All is not lost - I can still use a 2GB sd card that's been kicking around my place for months.  But 2GB ain't 4GB... and I haven't had this card very long, I'm gonna be seriously peeved if I have to stop using it!!

---

### Post by kartoshka on 2008-10-23
Sorry, I should have given a bit more detailed description.

fsck is a program that checks and tries to repair the filesystem on a given partition. It is really just a frontend for a number of other filesystem specific programs. e2fsck is the program responsible for checking/repairing ext2/3 filesystems, called by fsck. In my experience, most memory cards are FAT, not ext so e2fsck is not going to do any good.

The device name is the /dev entry that points to the physical piece of hardware in your computer. /media/... is just the folder the device is mounted on to give you access to the files it contains. When running fsck, you must provide the device name (/dev/whatever) not the mount point (/media/whatever).

I'm still not sure why fsck is not detecting the correct filesystem type. Run:
```
sudo mount
```
in the terminal and post the results here.

---

### Post by t0p on 2008-10-24
> **kartoshka said:**
>  Run:
```
sudo mount
```
in the terminal and post the results here.

Here's the output from *sudo mount*:

```
t0p@engine:~$ sudo mount
[sudo] password for t0p: 
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/t0p/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=t0p)
t0p@engine:~$ 
```

As you can see, the SD card does not appear.

To reiterate: I'm running hardy on an eeepc.  Up til now, I've had a 4 GB sdhc card permanently inserted in the card slot.  It has always auto-mounted fine every time I booted the computer.  Until now, that is.  Now, if I turn on the computer with the card inserted, the computer will not boot.  If I insert the card after the computer's booted, the card will not mount.  Earlier, I thought the computer could still detect the presence of the card: I was wrong.  It's as if the card does not exist.  Which is a real pain, as I have some files on that card that I hadn't backed up.  Dumb, I know, but that's the score.

I know the fault is with the card, not the eeepc, because it works fine with other sd cards.  It's just this one that's a problem.  And I've only had it a few weeks, so I am truly annoyed.  Is there any way I can "fix" this?

---

### Post by kartoshka on 2008-10-24
Ok it seems there were two distinct issues being discussed here, I got a little confused.

You're not the only one with this problem: [http://forum.eeeuser.com/viewtopic.php?id=28320](http://forum.eeeuser.com/viewtopic.php?id=28320)

The only suggestion in that thread was to update the BIOS firmware. Don't know if that will help in your case, but it may be worth a shot.

Did running:```
ls -la /media/MMCSD
```give you any results?

I don't know if this would help either, but I would try to remove the /dev/sbd1 entry from fstab, save and reboot. It may keep the system from hanging during boot with the card in the reader.

---

### Post by t0p on 2008-10-24
> **kartoshka said:**
> 
You're not the only one with this problem: [http://forum.eeeuser.com/viewtopic.php?id=28320](http://forum.eeeuser.com/viewtopic.php?id=28320)

The only suggestion in that thread was to update the BIOS firmware. Don't know if that will help in your case, but it may be worth a shot.

Yes, I read that thread.  I don't really understand what a BIOS update will do though.  My computer used to read this sd card with the old BIOS.  It can read other sd cards with the old BIOS.  I'm pretty sure the OP of that thread has the same problem as me:  a crap sd card.

> **kartoshka said:**
> 
Did running:```
ls -la /media/MMCSD
```give you any results?

Nope.

> **kartoshka said:**
> 
I don't know if this would help either, but I would try to remove the /dev/sbd1 entry from fstab, save and reboot. It may keep the system from hanging during boot with the card in the reader.

Yeah, I'll try that when I get home and can recharge the eeepc's battery.  In the meantime: does anyone out there know of a way that I can somehow *force* the computer to read the card?  So I can at least retrieve its contents?

---

### Post by kartoshka on 2008-10-24
The only other thing I can think of trying would be to try to mount it yourself in the terminal.

Try putting another SD card in the slot AFTER the computer is fully booted. Run "mount" at the terminal and take note of the device name (/dev/whatever) that is mounted at /media/MMCSD (or whatever the mount point is). Unmount/eject that card and remove it.

Put the SD card that's giving you trouble back in.

If it was FAT formatted (which IME is how sd cards are typically formatted):

```

mkdir /media/sdcard
sudo mount -t vfat /dev/DEVICE /media/sdcard

```

Where "DEVICE" is the thing you just made a note of above. Go to /media/sdcard and if that was at all successful, your files should be there. No idea if that will actually work, but it cant hurt. If by some chance the card uses a different filesystem, then replace "vfat" in the above mount command with the appropriate type (ext2, ext3, etc. There is a list if you look in "man mount").

There are ways to force mount if you know the filesystem type for sure, but if you're wrong, then any data that might be left could be completely wiped out. I do believe this has some success with corrupted filesystems tho, so it might be worth a shot. Unfortunately I have no personal experience with this procedure.

---

### Post by t0p on 2008-10-27
> **kartoshka said:**
> The only other thing I can think of trying would be to try to mount it yourself in the terminal.

Try putting another SD card in the slot AFTER the computer is fully booted. Run "mount" at the terminal and take note of the device name (/dev/whatever) that is mounted at /media/MMCSD (or whatever the mount point is). Unmount/eject that card and remove it.

Put the SD card that's giving you trouble back in.

If it was FAT formatted (which IME is how sd cards are typically formatted):

```

mkdir /media/sdcard
sudo mount -t vfat /dev/DEVICE /media/sdcard

```

Where "DEVICE" is the thing you just made a note of above. Go to /media/sdcard and if that was at all successful, your files should be there.

Nah...

> /dev/sdb1 is not a valid block device

Whatever that means...

> **kartoshka said:**
> 
There are ways to force mount if you know the filesystem type for sure, but if you're wrong, then any data that might be left could be completely wiped out. I do believe this has some success with corrupted filesystems tho, so it might be worth a shot. Unfortunately I have no personal experience with this procedure.

Can anyone help with forcing the card to mount?

---

