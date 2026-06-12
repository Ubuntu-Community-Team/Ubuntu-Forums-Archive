---
title: "USB memory stick keeps becoming read-only"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by t0p on 2008-07-07
I bought this USB flash memory stick a couple of months ago.  I noticed that, if I left it plugged in for a while, it would become read-only.  But, as it only happened if I left it in a while, and was easily fixed by remounting, I wasn't too bothered.

But now, it's becoming read-only nearly straight away.  I'll have time to save maybe 2 files, and that's it.

eg.
```
t0p@u-box:~$ cp wgetto.sh /media/disk/
cp: cannot create regular file `/media/disk/wgetto.sh': Read-only file system
```

I tried to change the stick's permissions, but it won't let me:
```
t0p@u-box:~$ sudo chmod 777 /media/disk
[sudo] password for t0p:
chmod: changing permissions of `/media/disk': Read-only file system

```

Any ideas how to fix this?

---

### Post by chrisccoulson on 2008-07-07
> **t0p said:**
> I bought this USB flash memory stick a couple of months ago.  I noticed that, if I left it plugged in for a while, it would become read-only.  But, as it only happened if I left it in a while, and was easily fixed by remounting, I wasn't too bothered.

But now, it's becoming read-only nearly straight away.  I'll have time to save maybe 2 files, and that's it.

eg.
```
t0p@u-box:~$ cp wgetto.sh /media/disk/
cp: cannot create regular file `/media/disk/wgetto.sh': Read-only file system
```

I tried to change the stick's permissions, but it won't let me:
```
t0p@u-box:~$ sudo chmod 777 /media/disk
[sudo] password for t0p:
chmod: changing permissions of `/media/disk': Read-only file system

```

Any ideas how to fix this?

If it is read-only, then no amount of chmod'ing will work. It's probably got errors on the filesystem. Being remounted read-only is a precautionary measure for a filesystem with errors in order to reduce the likelihood of further breakage. After it goes read-only, try this in a terminal:
```
cat /var/log/syslog | grep -i panic
```
...and see what comes out. If there are errors on the filesystem, then you will need to run a check in order to fix it. To do this (assuming it's a FAT32 volume):
```
sudo umount /media/disk
sudo dosfsck -a -v /dev/sdxx
```
...where /dev/sdxx is the device node for your USB memory stick

---

### Post by t0p on 2008-07-07
Thanks.  I ran **dosfsck** and got this:
```
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
         4 reserved sectors
First FAT starts at byte 2048 (sector 4)
         2 FATs, 16 bit entries
    125952 bytes per FAT (= 246 sectors)
Root directory starts at byte 253952 (sector 496)
       512 root directory entries
Data area starts at byte 270336 (sector 528)
     62957 data clusters (1031487488 bytes)
62 sectors/track, 32 heads
        63 hidden sectors
   2015168 sectors total
FATs differ but appear to be intact. Using first FAT.
Reserved field in VFAT long filename slot is not 0 (but 0xed).
Auto-setting to 0.
Start cluster field in VFAT long filename slot is not 0 (but 0x48fc).
Auto-setting to 0.
Unfinished long file name ":F4l:COZÿ:7Av:8u-:FZw:37r:3Vy:Eyn:Dl3:0lt:B-n:5pk".
  (Start may have been overwritten by \217ã\203ûM>Ÿ=.L\177\015)
  Not auto-correcting this.
Wrong checksum for long file name ":F4l:COZÿ:7Av:8u-:FZw:37r:3Vy:Eyn:Dl3:0lt:B-n:5pk".
  (Short name \217ã\203ûM>Ÿ=.L\177\015 may have changed without updating the long name)
  Not auto-correcting this.
Reserved field in VFAT long filename slot is not 0 (but 0xed).
Auto-setting to 0.d
Start cluster field in VFAT long filename slot is not 0 (but 0x48fc).
Auto-setting to 0.
Unfinished long file name ":F4l:COZÿ:7Av:8u-:FZw:37r:3Vy:Eyn:Dl3:0lt:B-n:5pk".
  (Start may have been overwritten by \217ã\203ûM>Ÿ=.L\177\015)
  Not auto-correcting this.
Wrong checksum for long file name ":F4l:COZÿ:7Av:8u-:FZw:37r:3Vy:Eyn:Dl3:0lt:B-n:5pk".

**[and it goes on like this]**
```

I'm guessing the problem is filenames that are too long?  Though I don't know where they came from... I certainly haven't named a file as ":F4l:COZÿ:7Av:8u-:FZw:37r:3Vy:Eyn:Dl3:0lt:B-n:5pk".

What do I have to do to rectify this? Will I need to reformat the stick.

Also: the dosfsck didn't complete. It stopped with the message:
```
Segmentation fault (core dumped)
```

What's *that* about?

---

### Post by philinux on 2008-07-07
I'd reformat the stick with fdisk or windows.

---

### Post by t0p on 2008-07-07
> **philinux said:**
> I'd reformat the stick with fdisk or windows.

I've read through the fdisk manpage, and couldn't find anything about reformatting.  Could someone give me a clue how to do it?

---

### Post by philinux on 2008-07-07
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

This has the best info for fdisk.

The final part of formatting if you only got one partition is probably all you need which is the mkfs.vfat command.

[http://linux.about.com/od/embedded/l/blcmdl8_mkfsvfa.htm](http://linux.about.com/od/embedded/l/blcmdl8_mkfsvfa.htm)

---

### Post by t0p on 2008-07-07
***Thanks*** philinux!

---

### Post by Ron Ruble on 2008-07-20
Very helpful; many thanks to Chris and Phil.

I just ran into the same issue, fewer errors and a dos filesystem check took care of everything.

Of course, I went down the wrong path first since I just picked up a USB hub; I was assuming the issue was related to that. ;>

---

