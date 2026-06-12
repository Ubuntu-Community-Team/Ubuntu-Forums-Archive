---
title: "Soo frustrated!  Cannot format partitions! Please Help."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by AbeBorker on 2008-08-27
Hi folks,

I'm a newcomer to linux, old hat with computers. I've been trying to solve this problem now for two days so I've caved and hoping that someone here will help me.

I have a Toshiba a15 sattelite that my dad thought was bricked, but I breathed new life into it and want to install ubuntu. I tried the live cd and loved it. I tried the Install from the liveCD and it went well until trying to partition my ext3 partition. Where it would hang up for hours.

I read online that the alternate CD might avoid the buggy partitioner, so I gave it a go. I tried the install and the "Partitions Formatting" screen stuck at 33%, reading "Creating ext3 file system / for in partition #1 of SCSI1 (0,0,0) *sda)..."

I hit Alt + RtArrow a few times to goto the log, and it's throwing out lines every few seconds. that look like this,

DATE : TIME : kernel: [ crazy long #'s ] ata1.100: status {DRDY ERR }
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: status {ABRT }
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: configured for PIO0
DATE : TIME : kernel: [ crazy long #'s ] ata1.: EH complete
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: Exception at Emask


and lots and lots of other things too! Honestly, it all moves so fast, it's hard to type in everything, I wish I had a way just to post it all without having to look over my shoulder and retype it! These are just five lines among many that show up. And after 30min or so, the status bar and screen are still the same....

I tried Standard and Advanced IDE in the BIOS, and I checked the CD, and I tried the LiveCD too, so I think it's not my CD. The HD is old, but I just was able to install WinXP on it two days ago.

I have now also tried the GParted LiveCD which I can't post a screenshot, but I'll try and describe what I tried... 
[HTML]<pre>
Partition        Filesystem    Label  Size
New Partition #1 ext3                 25.99 GB
New Partition #2 linux-swap    swap   1.95 GB</pre>[/HTML]

After pressing apply, GParted deletes my old unknown partion (from failed partitioning attempts) and then he process in bold under details appears to be:
mkfs.ext3 -L "" /dev/ (Creating the new filesystem)

Here GParted just hangs, status bar whizzing back and forth for the forseeable future.

Furthermore, upon canceling the formatting process, Gparted just stays "Scanning all devices" and I'm forced to do a hard reset...

I've tried ext2 partitions and I also tried a small ext3 partition to no avail!

I'm almost at the end of my rope.  I thought since I'm a beginner, it might help to post here.

---

### Post by northern lights on 2008-08-27
While I'm certain it's not the answer you were looking for, I'd say this sounds like you're Dad was right in at least the hdd being screwed...

---

### Post by AbeBorker on 2008-08-27
There's no question that the HDD has issues.  However!  there must be a way to get this sucker working.  I mean it's not the most reliable HDD, but I had no problems re-installing windows to grab all his files.

Is there any LiveCD with a good program to take a look at the hard drive.  If there was a troublesome section, could I just partition around it?  (I realize that might sounds like an absurd idea)

---

### Post by northern lights on 2008-08-27
> **AbeBorker said:**
> Is there any LiveCD with a good program to take a look at the hard drive.
fdisk should do. Present on the Ubuntu LiveCD...

> **AbeBorker said:**
> If there was a troublesome section, could I just partition around it?  (I realize that might sounds like an absurd idea)
That idea is not that absurd. If only a few specific sectors were broken, you could certainly do that. It ain't elegant, but far from absurd, nonetheless.

---

### Post by AbeBorker on 2008-08-27
I'm not so sure howto use fdisk.

I ran it in the terminal, "fdisk /dev/hda"
and it said unable to open /dev/hda

---

### Post by AbeBorker on 2008-08-27
I just found I was able to make a fat32 partition with ease!

---

### Post by cariboo on 2008-08-27
Try:

```
sudo fdisk /dev/hda
```

Jim

---

### Post by AbeBorker on 2008-08-27
I tried that, shoulda said so, sorry

---

