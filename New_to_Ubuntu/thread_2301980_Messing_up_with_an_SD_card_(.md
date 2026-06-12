---
title: "Messing up with an SD card :("
date: 2015-11-06
forum: New to Ubuntu
---

### Post by Dave_Berry on 2015-11-06
I'm running xubuntu and trying to mount an image on a SanDisk ultra 32GB empty disc. Getting a strange error;

```
dd: error writing ‘/dev/mcblk01’: No space left on device
360+0 records in
359+0 records out
1508716544 bytes (1.5 GB) copied, 16.1819 s, 93.2 MB/s
```

Which make no sense :(

I'm trying to mount an image using the following command;

```
sudo dd bs=4M if=/home/daveb/Downloads/2015-09-24-raspbian-jessie.img of=/dev/mcblk01
```

Saw a few posts, and thought including what fdisk gives me could help;

```
Disk /dev/mmcblk0: 31.1 GB, 31104958464 bytes
4 heads, 16 sectors/track, 949248 cylinders, total 60751872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba2edfb9

        Device Boot      Start         End      Blocks   Id  System
```

What have I screwed up guys!?

---

### Post by TheFu on 2015-11-06
dd is a dumb bit-for-bit copy tool. It has **nothing** to do with mounting. It can overwrite any data on any storage device easily when partnered with sudo. Be very careful.

If you want to copy an image to the SDHC device, then dd is the way.  Be certain that you have the correct target for the outputfile.

It appears the  of= parameter is wrong based on the fdisk output. Appears nothing bad happened this time. Lucky.

To "mount" storage, use the **mount** command.  It should require sudo to work.

---

### Post by Dave_Berry on 2015-11-07
So many thanks TheFu! I can't believe I missed that.

Altered my command and it works fine now! You're a star!

---

### Post by TheFu on 2015-11-07
Please mark as [solved] in the thread tools. This helps people who want to help and people looking for a solution.

That is a common mistake. I've made it a few times over the years.  It is especially hard for people not used to using CLI interfaces - we all know people whose eyes gloss over when there isn't a GUI to click. I was one of those people (oh so many years ago).

---

