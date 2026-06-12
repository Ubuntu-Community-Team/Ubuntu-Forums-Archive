---
title: "PLZ HELP!! Accidentally resized partition w/live cd!"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by lev5c on 2008-11-05
Here's the situation:
-------------------------------------------------
My intentions were to reinstall/upgrade to 8.10 in order to restore all default ubuntu settings (ATI drivers & video playback in particular :evil:), but keep personal data across all partitions. Now, I'm afraid I've screwed up the main linux partition in the process.

Here's what went down:
------------------------------------------------
1. Booted from 8.10 Live CD
2. Chose "Manual" hard drive partitioning
     It displayed the following: (sizes are approx)
      /dev/sda1    ext2          53gb      17gb used
      unallocated                 1gb
      /dev/sda2    linux-swap     2gb      ?
      /dev/sda3    ntfs          60gb      52gb used
      /dev/sda4    ntfs          40gb      37gb used

3. Resized sda1 to 25GiB

It did what I told it to do by unallocating space, I just assumed it would unallocate the 35 or so gigs of free space. Now, I can't boot cuz I'm getting a GRUB error 15: file not found. So, I have rebooted with the Live CD and ran partition manager.

It displayed the following: (sizes are approx)
      /dev/sda1    ext2          23gb      375Mb used
      unallocated                32gb
      /dev/sda2    linux-swap     2gb      ?
      /dev/sda3    ntfs          60gb      52gb used
      /dev/sda4    ntfs          40gb      37gb used

I tried the "undo changes to partitions" option to no avail, and that's exactly what I need to do. Been surfin' forums all day. Any help is appreciated. Thanks [-o<

---

### Post by nhasian on 2008-11-05
it sounds like your resizing went okay, but your MBR got messed up somehow.  you can fix it by using the supergrub disc:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lev5c on 2008-11-05
I have tried every SGD auto option there is and some others, but it won't repair or even recognize that there is a problem. And if resizing went ok, then the gb used on sda1 would be the same as before, no?

---

### Post by Paqman on 2008-11-05
Have you got a backup you can restore?

---

### Post by lev5c on 2008-11-05
Backup of what? MBR? boot folder? restore point? All data? Nope, nothing. ~Shoot me now.

---

### Post by lev5c on 2008-11-05
Surely there has to be a way to restore the partition. It's not like the data was deleted because it only took 20-30 seconds to unallocate it. Anybody have any ideas? I'm at a stand still.

---

### Post by bwang on 2008-11-05
Have you tried [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) ?

---

### Post by caljohnsmith on 2008-11-05
How about posting the full output of:
```
sudo fdisk -lu
```
Also post what happens when you do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
If the mount command gives you an error, try:
```
sudo fsck -y /dev/sda1
```
And then try mounting the partition again.

---

### Post by lev5c on 2008-11-05
Results for ```
sudo fdisk -lu
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7bc87bc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    48837599    24418768+  83  Linux
/dev/sda2       114993270   119186234     2096482+  82  Linux swap / Solaris
/dev/sda3       119186235   242067419    61440592+   7  HPFS/NTFS
/dev/sda4       242067420   320159384    39045982+   7  HPFS/NTFS


Results for ```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
total 48
drwxr-xr-x 2 root root 49152 2008-11-05 21:28 lost+found
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt

Now what?

---

### Post by lev5c on 2008-11-05
> **bwang said:**
> Have you tried [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) ?

The iso just finished downloading - I'm gonna try it now...[-o<

---

### Post by zwygart on 2008-11-05
If your Grub is broken try this,

# grub
Probing devices to guess BIOS drives. This may take a long time.

    GRUB  version 0.5.96.1  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> root (hd0,0)
 Filesystem type is ext2fs, using whole disk

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Running "install /boot/grub/stage1 d (fd0) /boot/grub/stage2 p /boot/grub/menu
.lst"... succeeded
Done.

grub> quit

Then reboot

If this not work, paste the last lines of the file (your drive)/boot/grub/menu,lst
The lines without #

I think 
root (hd0,0)
setup (hd0,0)

will do the job,

if not try setup this way : setup (hd0)

---

### Post by lev5c on 2008-11-05
grub> root (hd0,0)
Error 21: Selected disk does not exist

grub> setup (hd0,0)
Error 12: Invalid device requested

grub> setup (hd0)
Error 12: Invalid device requested

---

### Post by lev5c on 2008-11-06
I installed Testdisk and I have the Rescue Remix CD but I'm not sure if there's something I'm missing. Can someone give me some tips on how to use these programs to  "re"-allocate the space?

---

### Post by lev5c on 2008-11-06
> (via Google Groups)
So to make sure I understand you correctly; you wanted to "reinstall"
the OS itself, BUT save your personal files? (i.e. /home/username,
settings in /etc/... and the like) If that is the case, you will need
to rescue, as it is stating (by the error 15) that your partition or
location that it is looking for is "wrong".. bad or just not the File
System it was looking for. Boot with the CD and go to recovery mode
and try this:

chroot /mnt/sysimage
grub-install --recheck /dev/hda
exit
exit

:: What partition is the "important" data on? You may lose your
settings for ATI, and the like, but those are easily fixed, however
sensitive data is not..

That's exactly what I'm trying to do! I WANT the ati drivers/settings completely gone (among other things) and ubuntu back to default config, but I don't want to lose 3yrs of work, 40gigs of mp3s, and 60gigs of video. The "important (work) data" is in the unallocated space at the moment, but it used to be part of sda1 before I resized it.

Logged in to a Failsafe Terminal session and got this:
ubuntu@ubuntu:~$ chroot /mnt/sysimage
chroot: cannot change root directory to /mnt/sysimage: No such file or
directory

I am losing it here ](*,)

---

### Post by lev5c on 2008-11-06
Bumpskity bump I can't sleep till I fix this :(

---

### Post by caljohnsmith on 2008-11-06
According to the commands you ran in post #9, it looks like your Ubuntu sda1 partition mounted just fine, but the file system does not exist (at least the way it did before). The only folder you have in the sda1 directory is "lost+found", so if you're lucky, you may find some or all of your files there. How about doing:
```
sudo mount /dev/sda1 /mnt
gksudo nautilus &
```
That will open up a file browser as root user (be careful since it is root user), and if you navigate to the /mnt directory, you can look in the "lost+found" directory and see what's there. Hopefully your files will be there.

Try that first, and if you can't find your files in lost+found, you'll probably have to resort to file recovery software like [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). Let us know how it goes.

---

### Post by lev5c on 2008-11-06
Did exactly as you said. Empty. :confused:

There HAS to be a way to either: 
a.undo one (1) change to a partition's END
b.resize sda1 again to original size without overwriting data
c.combine sda1 and unallocated space to "re"allocate it
d.get some program to recognize that the partition has been resized

Haha maybe I need a lesson in partition theory but I don't wanna resort to actual "data recovery" just yet. This should be an easy fix :(

---

### Post by lev5c on 2008-11-06
I really don't want to lose my previous install, but I need to get back to work ASAP. Does anyone have any suggestions?

---

### Post by lev5c on 2008-11-07
Did a clean install of ubuntu 8.10. Resized partition to original ~55gigs. Oh well, at least my mp3s and video weren't lost. And, everything runs a sh*t ton faster now ;) Video and flash work once again!

---

