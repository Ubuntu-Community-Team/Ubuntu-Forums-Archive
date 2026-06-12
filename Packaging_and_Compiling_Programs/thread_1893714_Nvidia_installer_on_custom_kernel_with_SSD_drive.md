---
title: "Nvidia installer on custom kernel with SSD drive"
date: 2011-12-10
forum: Packaging and Compiling Programs
---

### Post by Bobhuber on 2011-12-10
OK here's what I trying to do. I've ordered a SSD drive and want to do most if not all my compiling in ram to conserve SSD writes. I've got 8/gig ram and have set up /tmp and /run/shm (used to be /dev/shm) in fstab to utilize the memory. Everything works fine and I am able to compile in the temp directories. The problem I'm having is in trying to install nvidia drivers on a custom kernel . After compiling the kernel  I'm trying to move the source directory to another drive (partition) and then create a sym link to the drive in  /lib/modules/<kernel version> so the Nvidia installer can find the source.Nvidia finds it OK and gets about halfway thru compiling the kernel headers and errors out. I look at the log and its giving a permissions error with a /scripts/recordmcount file in the source directory. I can move the source directory anywhere on the original drive and change the symlink to point to it and everything works fine. Permissions on the second drive are set to 777 and show correctly.

---

### Post by Bobhuber on 2011-12-11
> **Bobhuber said:**
> OK here's what I trying to do. I've ordered a SSD drive and want to do most if not all my compiling in ram to conserve SSD writes. I've got 8/gig ram and have set up /tmp and /run/shm (used to be /dev/shm) in fstab to utilize the memory. Everything works fine and I am able to compile in the temp directories. The problem I'm having is in trying to install nvidia drivers on a custom kernel . After compiling the kernel  I'm trying to move the source directory to another drive (partition) and then create a sym link to the drive in  /lib/modules/<kernel version> so the Nvidia installer can find the source.Nvidia finds it OK and gets about halfway thru compiling the kernel headers and errors out. I look at the log and its giving a permissions error with a /scripts/recordmcount file in the source directory. I can move the source directory anywhere on the original drive and change the symlink to point to it and everything works fine. Permissions on the second drive are set to 777 and show correctly.
FIXED > Added exec to fstab mount options on the partition.

---

