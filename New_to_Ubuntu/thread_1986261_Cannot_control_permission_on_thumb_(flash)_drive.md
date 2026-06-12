---
title: "Cannot control permission on thumb (flash) drive"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-05-24
I am setting up Lastpass. I am using Sesame. I have d/l'd the sesame archive, unpacked it and copied the sesame an external USB thumb or flash drive. The drive has about 1.5 gig free space.

Opening a terminal and 

cd /media/thumbdrive

shows the drive's name and ls shows

sesame

doing:

./sesame

shows:


mark@Lexington-19:/media/Lexar$ ./sesame
bash: ./sesame: Permission denied

so I opened Thunar, and looking at the permissions tried to set sesame to "allow to run as program". But the moment I moved the mouse cursor away from the checkbox/line the checkmark in the box reverted to blank or empty. Next, running gksudo thunar, I tried the same. But rather than offering a "run as program" it showed the group username as having no permission to read/write. Trying to change that to read/write asks for "apply recursively" and I said Yes. OS hummed for a moment and then the read/write under group went back to blank or no permissions for the group member.

What gives?

And, most simply, how can I run the executable "sesame" on an external drive?

---

### Post by papibe on 2012-05-24
Hi Mark_in_Hollywood.

Could you post the result of these commands?
```
cd /media/Lexar

ls -l

file sesame
```
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-25
The relevant part of ls -l is:



-rw------- 1 mark mark   3414068 May 15 09:05 sesame
-rw------- 1 mark mark   1292588 May 24 13:36 sesame.tar.bz2

Neither 'chmod +x sesame' or, 'sudo chmod +x sesame' have changed the file permissions.

---

### Post by cortman on 2012-05-25
If the drive is formatted to NTFS, Linux file permissions won't work. What is the drive's format?

---

### Post by papibe on 2012-05-25
You missed one command.
```
file sesame
```
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-28
Terminal output:

mark@Lexington-19:/media/Lexar$ file sesame

sesame: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

OK, so, how does this work?

PS - I am running a 32-bit Precise Pangolin.

---

### Post by papibe on 2012-05-28
Thanks.

I belive cortman diagnostic is correct. Your flash drive is NTFS formated. There are 2 ways to change the permissions. Play with the command line and change the mount options, or install 'NTFS Configuration Tools' from the Software Center (with a GUI).

For the mount options take a look at post #8 of this [thread]("http://ubuntuforums.org/showthread.php?t=1204763"). In your case, umask=022 will be enought to do the trick.

Here's an still usefull, although old looking, [tutorial]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") for the GUI option.

I hope that helps, and tell uf how it goes. 
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-30
I found the NTSF config in the USC. Upon running, it crashed, so that avenue isn't open for me right now. Moreover, the partitions found by the NTFS config don't show the thumb drive (flash drive, usb drive -- too many synonyms) as accessible. So, even with NTFS config, the device isn't available.

I guess in time the NTFS config may get fixed, but for now, please stop replying to my post. I won't mark it solved, but I can't go forward with it, either.

ALSO, I tried umask=22. First I umount'd /dev/sde (the Lexar device)

The terminal said:

mark@Lexington-19:/dev$ sudo mount /dev/sde /media/Lexar -t ntfs -o uid=1000,gid=1000,umask=22
NTFS signature is missing.
Failed to mount '/dev/sde': Invalid argument
The device '/dev/sde' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mark@Lexington-19:/dev$ 

Thanks, Linux Community.

---

### Post by papibe on 2012-05-30
Could you post the result of this commands with USB plugged?
```
df -h

sudo fdisk -l
```
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-30
papibe: I can only guess by "usb unplugged" that you mean the device (Lexar thumbdrive) that I was attempting to run the sesame executable on, rather an all the USB devices. I ran the commands with the Lexar unplugged, as you can see, below. I can unplug and redo the df -h and sudo fdisk -l if you want with all the USB devices removed.

Meanwhile, I have looked at an 8-gig thumbdrive, downloaded a 'fresh' tarball to it, extracted the sesame executable, only to have the exact same problem. The 8-gig is partitioned MBR and the FAT is FAT32, according to (Linux) Disk Utility. /dev/sda1 is the win7 boot partition and the /dev/sda2 is the windows equivalent of the linux /home. The /dev/sda5 is my linux /home and /dev/sdc1 is a thumbdrive formatted for linux as ext3.

I hope this helps.

ALSO, I occasionally have a window popup on (or over) the desktop asking for my (boot time) password. This request is after the boot-time login at bootup that is the common password entry time for a user session. Usually, this inconsistently occurs when I call Chrome.

mark@Lexington-19:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        15G  8.2G  5.5G  61% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  956K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  2.1M 1005M   1% /run/shm
/dev/sda1       100M   25M   76M  25% /media/System_Reserved
/dev/sda2        69G   44G   25G  65% /media/sda2
/dev/sda5       278G   62G  202G  24% /home
/dev/sdc1       947M  116M  784M  13% /media/5c9a6ed1-2994-4549-b87c-735f94f1cb55
mark@Lexington-19:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143566847    71680000    7  HPFS/NTFS/exFAT
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

Disk /dev/sdd: 257 MB, 257949696 bytes
8 heads, 62 sectors/track, 1015 cylinders, total 503808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdd4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 1010 MB, 1010826752 bytes
228 heads, 40 sectors/track, 216 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              40     1969919      984940   83  Linux

---

### Post by papibe on 2012-05-30
Sorry If I was unclear, but I meant with the Lexar USB plugged so the commands I gave you show its actual device name.

Regards.

---

### Post by Mark_in_Hollywood on 2012-05-30
mark@Lexington-19:/media/LEXAR$ df -h
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        15G  8.2G  5.5G  61% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  964K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  2.4M 1005M   1% /run/shm
/dev/sda1       100M   25M   76M  25% /media/System_Reserved
/dev/sda2        69G   44G   25G  65% /media/sda2
/dev/sda5       278G   62G  202G  24% /home
/dev/sdc1       947M  116M  784M  13% /media/5c9a6ed1-2994-4549-b87c-735f94f1cb55
/dev/sdb1       3.7G  879M  2.9G  24% /media/LEXAR
mark@Lexington-19:/media/LEXAR$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143566847    71680000    7  HPFS/NTFS/exFAT
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

Disk /dev/sdd: 257 MB, 257949696 bytes
8 heads, 62 sectors/track, 1015 cylinders, total 503808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdd4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 1010 MB, 1010826752 bytes
228 heads, 40 sectors/track, 216 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              40     1969919      984940   83  Linux

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              62     7700151     3850045    c  W95 FAT32 (LBA)


ALSO, ,using gksudo Thunar, I just tried to "Extract Here" via right click on the tarball and got this response:


tar: sesame: Cannot change ownership to uid 1010, gid 1010: Operation not permitted
tar: Exiting with failure status due to previous errors

Does this help???

---

### Post by papibe on 2012-05-30
Yes. It does.

First unmount the Lexar drive:
```
sudo umount /media/LEXAR
```
Then remount it:
```
sudo mount -t fat32 /dev/sdb1 /media/LEXAR -o uid=1000,gid=1000,umask=022
```
Tell us how it goes.
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-30
Honestly, I'm starting to think I have ghosts in this 'puter.

Results:


mark@Lexington-19:/media$ sudo umount /media/LEXAR
[sudo] password for mark: 
mark@Lexington-19:/media$ ls
5c9a6ed1-2994-4549-b87c-735f94f1cb55  sda2  System_Reserved

No LEXAR mounted

mark@Lexington-19:/media$ sudo mount -t fat32 /dev/sdb1 /media/LEXAR -o uid=1000,gid=1000,umask=022
mount: mount point /media/LEXAR does not exist

???

Ahhhh... so sorry, I thought maybe the problem is with this LEXAR being plugged into a USB hub. SO, I plugged it into the computer's usb port w/o anything 'in between'.

sudo fdisk -l shows:

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e


mark@Lexington-19:/media/LEXAR$ sudo mount -t fat32 /dev/sdb1 /media/LEXAR -o uid=1000,gid=1000,umask=022
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
mark@Lexington-19:/media/LEXAR$

---

### Post by papibe on 2012-05-30
We are getting close ;)

```
sudo mkdir /media/LEXAR

sudo mount -t fat32 /dev/sdb1 /media/LEXAR -o uid=1000,gid=1000,umask=022
```

Tell us how it goes.
Regards

---

### Post by Mark_in_Hollywood on 2012-05-30
mark@Lexington-19:/media/LEXAR$ sudo mkdir /media/LEXAR
mkdir: cannot create directory `/media/LEXAR': File exists

mark@Lexington-19:/media/LEXAR$ sudo mount -t fat32 /dev/sdb1 /media/LEXAR -o uid=1000,gid=1000,umask=022
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
mark@Lexington-19:/media/LEXAR$

---

### Post by papibe on 2012-05-30
Try mounting it on a different location:
```
umount /media/LEXAR
cd
mkdir mnt
sudo mount -t vfat /dev/sdb1 mnt/ -o uid=1000,gid=1000,umask=022

```
Regards.

---

### Post by Mark_in_Hollywood on 2012-05-30
mark@Lexington-19:/$ umount /media/LEXAR
mark@Lexington-19:/$ cd
mark@Lexington-19:~$ sudo mount -t vfat /dev/sdb1 mnt/ -o uid=1000,gid=1000,umask=022
mount: mount point mnt/ does not exist
mark@Lexington-19:~$

ooopppsss, my bad, I didn't mkdir, first.

mark@Lexington-19:~$ mkdir mnt
mark@Lexington-19:~$ sudo mount -t vfat /dev/sdb1 mnt/ -o uid=1000,gid=1000,umask=022
mark@Lexington-19:~$

OK, here's where I have got to:

mark@Lexington-19:/$ cd /mnt
mark@Lexington-19:/mnt$ ls
mark@Lexington-19:/mnt$ 

mark@Lexington-19:/mnt$ cd /media
mark@Lexington-19:/media$ ls
5c9a6ed1-2994-4549-b87c-735f94f1cb55  sda2  System_Reserved

mark@Lexington-19:/media$ sudo ls
5c9a6ed1-2994-4549-b87c-735f94f1cb55  sda2  System_Reserved
mark@Lexington-19:/media$

no LEXAR? BUT, LEXAR shows up in Thunar file list AND, I d/l'd the sesame executable there and was able to call it from the Thunar gui and it is WORKING!. So, sir, a mighty thank you for sticking with me this afternoon. In about an hour I'll mark this as solved. (giving myself time in case the LastPass 2 step authentication balks at LEXAR).

---

### Post by Mark_in_Hollywood on 2012-05-30
So, after an hour or so of having the LEXAR show the sesame executable in it's GUI, I ran it several times until I figured some of it out. At least I could login to the lastpass account.

I moved the data I don't want hacked or viewed back onto the removable drive and pulled it out of the USB socket on the computer.

Then I saw that by removing the drive, the login to LastPass was logged out. Nice safety feature. BUT, when I plugged the LEXAR back into the computer's usb hub, (Bus 001 Device 019: ID 05dc:a769 Lexar Media, Inc.) - I cannot execute sesame. Right clicking on it call "." as the means to execute it. That should be ./ - ahh that's a . without the quotes.

From a termnal, LEXAR is now in /media. But doing: cd /media/LEXAR and then ./sesame returns the same permission errors as before.

How can I tell the executable to not use the "."? Or any other program?

and

mark@Lexington-19:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        15G  8.2G  5.5G  61% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  968K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  1.9M 1005M   1% /run/shm
/dev/sda1       100M   25M   76M  25% /media/System_Reserved
/dev/sda2        69G   44G   25G  65% /media/sda2
/dev/sda5       278G   61G  203G  24% /home
/dev/sdc1       947M  116M  784M  13% /media/5c9a6ed1-2994-4549-b87c-735f94f1cb55
mark@Lexington-19:~$ 
mark@Lexington-19:~$ 
mark@Lexington-19:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143566847    71680000    7  HPFS/NTFS/exFAT
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

Disk /dev/sdd: 257 MB, 257949696 bytes
8 heads, 62 sectors/track, 1015 cylinders, total 503808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdd4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 1010 MB, 1010826752 bytes
228 heads, 40 sectors/track, 216 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              40     1969919      984940   83  Linux

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              62     7700151     3850045    c  W95 FAT32 (LBA)
mark@Lexington-19:~$

---

