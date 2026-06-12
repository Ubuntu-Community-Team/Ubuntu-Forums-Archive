---
title: "Solved: &quot;Mounting Local Filesystems&quot; fails after compiling new kernel"
date: 2005-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by vyruss on 2005-12-15
I've noticed that many people get "**Mounting Local Filesystems ... Failed**" at boot when trying out their newly-compiled kernel and so did I. Here's a tip that worked like a charm for me. 

It appears that the new 2.6 series kernels do not like the Enterprise Volume Management System (EVMS) that our beloved Breezy uses. So here's how to compile your kernel to avoid getting this error by applying the relevant kernel patch:

First, you need to install package **kernel-patch-evms** through Synaptic or apt-get or whatever you like to use. This installs the patch in **/usr/src/kernel-patches/**.

Then, before compiling your kernel, go to **/usr/src/linux/**, or wherever you keep your kernel source to be compiled, and run this in order to patch the kernel:```
sudo gzip -d 2.6-bd-claim.patch.gz
sudo cat /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch | patch -p1
```Then compile your kernel as usually and everything will be fine :)

I tried this with a "vanilla" 2.6.14 kernel from kernel.org, applied the patch, and then applied the Con Kolivas -ck6 patch for enhanced performance and it worked perfectly.

Happy compiling!

---

### Post by Bloot on 2005-12-17
I tried this but still can't mount volumes.

I had to extract the package contained in /usr/src/kernel-patches/diffs/evms-bd-claim, and then applied the patch to get it working

```
sudo cat /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch | patch -p1
```

It's so frustrating to compile a new kernel and then can't be able to mount the volumes...

---

### Post by vyruss on 2005-12-17
[QUOTE=Bloot]I had to extract the package contained in /usr/src/kernel-patches/diffs/evms-bd-claim, and then applied the patch to get it working[/QUOTE]

Oops, you're right, copy/paste mistake. Fixed now.

---

### Post by Zubzub on 2006-03-04
I realise this might be some necro-posting, but I can't seem to figure out my problem...

The problem I have is the next one:
I dld the latest stable kernel (from kernel.org, 2.6.15)
I patch it with the evms patch
I patch it with the latest ck patch
I compile, everything works great
well almost...

It seems I don't have script exec rights on my partitions (even when I run as root). Altough my fstab file enables exec and when I check my partitions in kubuntu, it all says enable exec, yet when I type "mount" it says noexec... 
When I start evmsgui, it also give me en error:

Mar 04 13:45:03  DosSegMgr: Warning:  Using an alternate geometry (Cylinders, Heads, Sectors) for drive hda.
The kernel reported drive geometry is: C= 65535 H= 16 S= 63
The partition records report a geometry of: C= 65535 H= 255 S= 63
Using the alternate geometry reported by the partition records.

evms sees all my paritions yet can't seem to edit them...

I also notice during booting that it gives certain mounting errors (where it says it will mount as read-only...:???: )

help:(

---

### Post by Kalimar on 2007-06-04
I think what you have posted may solve my problem!  Being a newbie to the LINUX environment, I don't always know where I need to be editing things. This is particularly true now, that I am booting from a LIVE CD but mounting a kernel afterwards (i.e. the kernel that won't boot). I have learned how to edit the correct FSTAB file but how do I apply the EVMS  patches to a kernel that doesn't boot and can only be mounted after booting from the live CD? Allow me to include the output from the blkid command and also fdisk -l. II don't have any settings in FSTAB yet for the EVMS.Thanks so much for your help on this.

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ sudo blkid
/dev/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"

---

