---
title: "[SOLVED] Hard drive turned into garbled filenames and unreadable files!"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by lookitseman on 2008-09-04
I figure no matter what I come across, I'm not the first, and I'm not the last...the answer has to be somewhere, but I have met my match, because in this case, I don't want to make a wrong step.  With that said...

This is what an ls on my external hard drive looks like (abridged):
```

&#9524;.&#9500;
&#9496;.&#9608;
!.#
).+
±.&#8804;
.
&#9618;.&#9474;
&#9571;.&#9559;
&#9556;.&#9574;
&#9572;.&#9561;

....
....


at.ct
at.ct
at.ct
at.ct
at.ct
at.ct
at.ct
a	t.c	t
a
t.c
t
at.ct
at.ct
a
t.c
t
at.ct
at.ct
at.ct
at.ct
at.ct
at.ct
at.ct
....
....

í&#9632;s.ú&#9632;s
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
i	t.k	t
i
t.k
t
it.kt
it.kt
i
t.k
t
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.kt
it.Kt
it.Kt
it.Kt
it.Kt
it.Kt
it.Kt
....

```

You see the problem.  I searched around, and found out about fsck and dosfsck, but neither helped.  I ran fsck against the unmounted drive.

```
 sudo fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

and i don't even know if dosfsck is appropriate in this case, but it wasn't any help.  Fat32 isn't an ext2 filesystem is it?

I think the problem was caused when I was pulling data off of my home network onto my hard drive.  I first noticed the problem once the drive moved to my other laptop, running Windows XP (hence the reason for FAT32).  I *think* after I pulled down the data, but before I moved the drive to the other laptop...the hard drive was fully functional.

Now every time I access the drive, what I see changes, I can't open any files, I can see the folder names at the hard drive root (amongst hundreds of junk entries like the ones above), but subfolders are either missing or have garbled titles.

I'm open for suggestions...what steps does one take to try to diagnose a hard drive???

---

### Post by Pelham123 on 2008-09-04
I had a similar problem with an XP box. I used this utility 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

that enabled me to recover my files. The bootsector/partition table was corrupted.

Hope this helps

---

### Post by Whiffle on 2008-09-04
What brand?  I had to deal with an external 250GB MAxtor this summer with similar symptoms.

---

### Post by lookitseman on 2008-09-04
Thanks for the quick replies...

It's a Lacie 250GB.

I'll take a look into that program you linked me to and let you know how it goes.

---

### Post by efalk on 2008-09-06
I had the same problem!

I have a USB disk that was used to back up a BSD system.  The data on it is very valuable, so I'm terrified to run any utilities on it.

I plugged it into my Ubuntu system and had the same results.  My fear is that the Ubuntu system mistook the partition table for something else, auto-mounted the drive as a DOS drive (or something) and read back gibberish.  My fear is that when I unmounted the drive, something may have been written back to it, corrupting it.

UFS support is compiled as a module, which was *not* loaded at the time.

Here is what I've done:

Unplug the USB cable

Disabled auto-mounting of new media

modprobe ufs

Plug in the USB cable

/var/log/messages shows this:

```
kernel: [19737393.372000] usb 5-7: new high speed USB device using ehci_hcd and address 12
kernel: [19737393.504000] scsi6 : SCSI emulation for USB Mass Storage devices
kernel: [19737398.504000]   Vendor: WD        Model: 5000AAC External  Rev: 1.65
kernel: [19737398.504000]   Type:   Direct-Access                      ANSI SCSI revision: 04
kernel: [19737398.504000] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
kernel: [19737398.508000] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
kernel: [19737398.508000]  sdc: sdc1
kernel: [19737398.520000]  sdc1: <bsd:bad subpartition - ignored
kernel: [19737398.520000]  >
kernel: [19737398.520000] sd 6:0:0:0: Attached scsi disk sdc
kernel: [19737398.520000] sd 6:0:0:0: Attached scsi generic sg2 type 0
```

That message about "bad subpartition - ignored" is very suspicious to me.

fdisk shows this:

```
# fdisk /dev/sdc
This disk has both DOS and BSD magic.
Give the 'b' command to go to BSD mode.

Command (m for help): p

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60800   488375968+  a5  FreeBSD

Command (m for help): b

Reading disklabel of /dev/sdc1  at sector 64.

BSD disklabel command (m for help): p

8 partitions:
#       start       end      size     fstype   [fsize bsize   cpg]
  a:        1*    60800*    60799*    4.2BSD     2048 16384 28528
  c:        1     60800*    60799*    unused        0     0

```

Any attempts to mount /dev/sdc1 met with messages like "ufs_read_super: bad magic number".  I'm guessing that the line that sayd "bad subpartition" should actually have listed the bsd partitions (e.g. /dev/sdc5) which would have been what I mounted.

Any idea how I should proceed?  The only thing I can think of at this point is to install FreeBSD on my system (maybe under vmware) and try mounting the drive natively.

---

### Post by efalk on 2008-09-09
bump

---

### Post by efalk on 2008-09-11
Well, as far as my system not recgonizing the BSD partition goes; I was able to get it to work by manually creating a logical partition for the file system:

```
dmsetup create mydisk << EOF
0 976751921 linear /dev/sdc1 16
EOF

mount -r -t ufs -o ufstype=ufs2 /dev/mapper/mydisk /mnt/tmp
```

I'm still not understanding why my system refused to recognize the FreeBSD partitions.

---

### Post by lookitseman on 2008-09-13
That program is amazing.  I was able to fix my drive.

THANKS!!!

---

