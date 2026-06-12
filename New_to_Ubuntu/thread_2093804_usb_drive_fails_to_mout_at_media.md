---
title: "usb drive fails to mout at /media"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-11
Hello all,
 
When I insert a usb flash drive, it fails to automount.  If I mount the drive at /media/part1, it mounts and the sidebar shows the icon for the drive.  I have checked to make sure that automount is turned "on", and it is.  What is going on?
 
Cheers,
Mark Allyn

---

### Post by aliddell on 2012-12-11
Have you seen [this post]("http://ubuntuforums.org/showthread.php?t=1620555")? With your usb drive unmounted and out, what is the output of
```
ls -l /media/
```?

---

### Post by mark allyn on 2012-12-12
Good morning, Aliddell,

OK, here's the listing:

administrator@ubuntu:~$ ls -l /media
total 17
drwxr-xr-x 2 root root 1024 Dec  5 17:47 crud
drwxr-xr-x 2 root root 1024 Dec  5 17:40 firstpart
drwxr-xr-x 2 root root 1024 Dec  5 15:36 part1
drwxr-xr-x 3 root root 4096 Dec 10 15:23 part2
drwxr-xr-x 2 root root 4096 Dec  5 11:41 SandiskSec
drwxr-xr-x 2 root root 1024 Dec 10 16:21 sdb2
drwxr-xr-x 2 root root 1024 Dec 10 16:26 sdb5
drwxr-xr-x 2 root root 1024 Dec 10 16:26 sdb6
drwxr-xr-x 2 root root 1024 Dec 10 18:01 sdc2
drwxr-xr-x 2 root root 1024 Dec  5 17:41 secondpart
drwxr-xr-x 2 root root 1024 Dec  5 15:07 usbflash2

Some explanation.  Part1, part2, sdb2, sdb5, sdb6, and sdc2, secodnpart, usbflash2, are all the same flash drive.  SandisksSec is a different flash drive.  It works fine when plugged.--automounts just as it should.  When I remove SandisksSec from its plug (after umounting it), its entry in /media goes away.  When I remove part1--etc--those directories in /media do not go away.  BTW, par2, etc.  DO show up with sudo blkid and with fdisk -l, so the machine is definitely aware of the flash.  It just can't automount.

I read the links you sent, but couldn't quite figure out what I was supposed to be looking for.

Thanks for your help on this.  It's a small issue, but for some reason it is really bothersome.

Regards,
Mark Allyn

---

### Post by sudodus on 2012-12-12
Have you made an entry (or several entries) for the troublesome USB drive in the file

```
/etc/fstab
```

And what about the partitions? Please post the contents of those commands:

```
sudo blkid
```
```
sudo fdisk -lu
```
```
cat /etc/fstab
```
and when the drive is mounted:
```
cat /etc/mtab
```

This might help us find the problem.

---

### Post by mark allyn on 2012-12-12
Good afternoon, Sudodus,

WITHOUT the flakey flash drive plugged, here are the results

administrator@ubuntu:~$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk  none         swap  sw        0  0  


administrator@ubuntu:~$ sudo blkid
[sudo] password for administrator: 
/dev/loop0: UUID="9b16030c-08f8-4f5d-b228-63e13bca7839" TYPE="ext3" 
/dev/sda1: LABEL="SYSTEM" UUID="64CE541ACE53E33A" TYPE="ntfs" 
/dev/sda2: UUID="4658112F58111F6D" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="F46E6A2A6E69E5B8" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="6459-E50D" TYPE="vfat" 
administrator@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5147c726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   589488127   294435840    7  HPFS/NTFS/exFAT
/dev/sda3       589490176   620947455    15728640    7  HPFS/NTFS/exFAT
/dev/sda4       620947456   625131519     2092032    c  W95 FAT32 (LBA)
administrator@ubuntu:~$ cat /etc/mtab
/dev/loop0 / ext3 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda2 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/administrator/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=administrator 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
administrator@ubuntu:~$ 

WITH the flakey flash plugged in, results are as follows:
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk  none         swap  sw        0  0  


administrator@ubuntu:~$ sudo blkid
/dev/loop0: UUID="9b16030c-08f8-4f5d-b228-63e13bca7839" TYPE="ext3" 
/dev/sda1: LABEL="SYSTEM" UUID="64CE541ACE53E33A" TYPE="ntfs" 
/dev/sda2: UUID="4658112F58111F6D" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="F46E6A2A6E69E5B8" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="6459-E50D" TYPE="vfat" 
/dev/sdb2: LABEL="part2" UUID="1bb1630a-9fa4-4030-82e8-5b8fd8a0f0ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="part5" UUID="bba157e4-26b1-4ed0-a45d-e1ffc19054c8" TYPE="ext4" 
/dev/sdb6: LABEL="part6" UUID="fef164ef-add2-4895-8280-7222949f2211" TYPE="ext4" 
administrator@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5147c726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   589488127   294435840    7  HPFS/NTFS/exFAT
/dev/sda3       589490176   620947455    15728640    7  HPFS/NTFS/exFAT
/dev/sda4       620947456   625131519     2092032    c  W95 FAT32 (LBA)

Disk /dev/sdb: 8036 MB, 8036285952 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000029c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     6148095     3073024    5  Extended
/dev/sdb2         7309312    11405311     2048000   83  Linux
/dev/sdb5            6144     1030143      512000   83  Linux
/dev/sdb6         2052096     5126143     1537024   83  Linux

administrator@ubuntu:~$ cat /etc/mtab
/dev/loop0 / ext3 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda2 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/administrator/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=administrator 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
administrator@ubuntu:~$ 

administrator@ubuntu:~$ 


I should also describe one other symptom as it might help you untangle this knot.  Clicking the mouse doesn't work for a minute or so after plugging in the flakey flash...nothing happens.

I don't understand the sequence of events that ensue when automount is executed.

I certainly hope you can figure this thing out.  Thanks for trying.

Cheers,
Mark Allyn

---

### Post by sudodus on 2012-12-12
I see the loop mount and that /dev/sda2 is mounted on /host
so I conclude that you are running Ubuntu in a wubi install. I can understand that, since the windows installation already occupies all four available primary partitions. But wubi is not as stable as a standard or dual-boot installation of Ubuntu (with or without Windows alongside).

I cannot find any obvious reason why there should be problems.

It would help if you can boot your computer into a live session directly from an install drive, a boot USB/CD/DVD drive with Ubuntu, Lubuntu or Xubuntu. Maybe something is corrupted in your system. Maybe it is the USB drive that is somewhat strange (hardware or software). So a series of questions/suggestions might help you 'via trial and error'.

What is stored on this USB flash drive? Are there operating systems? Is it bootable?

Do you have another USB drive (flash, HDD ...) or flash card in a camera or mobile phone?

Is your Ubuntu installation new or old?
Have you had this problem all the time?
Is some other USB drive mounting properly?
Is this USB drive mounting properly in another computer with Linux (the ext file systems are not recognized by Windows unless you add some special software).

---

### Post by mark allyn on 2012-12-12
Good afternoon, Sudodus,

Yes, this is a WUBI installation as you surmised.  It is WUBI for exactly the reason you mention.  As an aside, I have invested in an external hard drive on which to install UBUNTU exclusively.  If that doesn't work well I'll throw in the towel and kill of the restore partition---but this is a last resort.

Your other questions:

1.  This WUBI install is about a month old.
2.  Other flash drives work fine on all the sockets.  The flakey flash drive works on NONE of the sockets properly.
3.  All that is on the flakey drive are some small text files.  No operating systems.  It's not bootable.
4.  I do have another "pure" 12.04.1 installation on another HP box.  I like your idea about trying the flakey one out on that system.  I will go out to the barn where it sits and try it out.  I'll get back with the answer.
5.  It is possible that this particular flash drive is simply no good for some reason...


Thanks for digging into this.

Mark Allyn

---

### Post by mark allyn on 2012-12-12
Hello once more, Sudodus,

Well, matters become cloudier still.  Or maybe not.  I tried the flakey drive on the "pure UBUNTU installed" 12.04.1 machine and it automounted with no trouble.

It's really hard for me to see why this particular USB flash should fail on this particular machine when everything else works...

Hmmmm.

Cheers,
Mark Allyn

---

### Post by sudodus on 2012-12-13
> **mark allyn said:**
> Hello once more, Sudodus,

Well, matters become cloudier still.  Or maybe not.  I tried the flakey drive on the "pure UBUNTU installed" 12.04.1 machine and it automounted with no trouble.

It's really hard for me to see why this particular USB flash should fail on this particular machine when everything else works...

Hmmmm.

Cheers,
Mark Allyn

Well, I think there is sometimes strange with this particular 'flaky' USB flash drive. And I think there is something strange with that particular computer with the wubi install. And the result is that they won't cooperate well enough to automount.

You could re-partition and re-format the flaky USB drive using gparted. If that helps it was a software problem. Otherwise it may be a hardware problem (of the flash drive).

You could boot the computer into a live session with your Ubuntu boot drive, and check if that makes it possible to automount this flaky USB drive.

---

### Post by mark allyn on 2012-12-13
Good mosrning, Sudotus,

I will try the repartitioning idea and see if it matters.  Right now there is an extended partition with two logical partitions and a primary.  I'll delete everything except the primary and see what happens.

I'll let you know.

Cheers,
Mark Allyn

---

### Post by mark allyn on 2012-12-13
Good morning, again, Sudotus,

I deleted all partitions except for a primary with ext3 on it.  No dice.  I can mount it to /media/part2 "by hand" and the icon shows up on side bar but no automount happens.

phooey.

Thanks for your help on this, however.

Regards,
Mark Allyn

---

### Post by sudodus on 2012-12-13
Start from the very beginning by deleting everything. Use gparted:

Device -- Create Partition Table ... (select MSDOS alias MBR)

or something of that meaning (I don't have it in English)

and after that you create one or more partitions.

---

### Post by mark allyn on 2012-12-13
Good afternoon Sudodus,

Sorry I've been spelling your name incorrectly.  Is it possible that your name is derived from Zero Mostel's name "Psudolus" in "A Funny Thing Happened on the Way to the Forum"?

Cheers

---

### Post by sudodus on 2012-12-13
> **mark allyn said:**
> Good afternoon Sudodus,

Sorry I've been spelling your name incorrectly.  Is it possible that your name is derived from Zero Mostel's name "Psudolus" in "A Funny Thing Happened on the Way to the Forum"?

Cheers
It's from sudo with mirroring to make it a palindrome.

---

### Post by mark allyn on 2012-12-13
Good afternoon, Sudodus,

I deleted all partitions, and still no automount.

Ah yes....a palindrome.  Should have seen that.

Cheers.
Mark

---

### Post by sudodus on 2012-12-14
Good morning Mark,

Still no automount (!)

I assume that you did create a new partition table and at least one new partition with a file system in it? Otherwise there is nothing to mount.

If this is so, I think the pendrive itself is strange. I would not say bad, but such that it does not completely cooperate with your wubi system. Pendrives are different on the hardware and firmware level, almost all of them work properly to store data, most of them can be made into boot drives, but some of them can't do everything you'd expect.

---

### Post by mark allyn on 2012-12-14
Good morning, Sudodus,

Yes, I created a new partition and it didn't automount.  Moreover, the flash drive continues to lock out the keyboard and the mouse for about 2-3 minutes after it is inserted.

So...I think we give this up to the gods and let it go.

After all, I only gave 8 bucks for it.

Thanks for your patience and help.

Mark

---

### Post by sudodus on 2012-12-14
You are welcome :-)

---

