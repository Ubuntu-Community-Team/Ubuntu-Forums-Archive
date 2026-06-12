---
title: "Please help me Remount my External Hard Drive again."
date: 2011-10-29
forum: New to Ubuntu
---

### Post by mikodo on 2011-10-29
Please help me re-mount my external hard drive. I wasn't paying attention and reformatted it live. Luckily, there wasn't anything on it.

I want it to automount when I start the hard-drive again to /media/dev/sdf1,or <UUID> (I think that is how it was mounted to the the tree before).

Below is a screenshot that shows a Warning about the External Hard Drive: 

Unable to find mount point
Unable to read the contents of this file system!
Because of this some operations may be unavailable.


A couple of commands to see my system. The /dev/sdf1 is the external hard drive that is not mounted.


mikodo@mikodo-desktop:~$ sudo fdisk -l
[sudo] password for mikodo: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002efb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       38119   286658067+  83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce5ab5a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux


mikodo@mikodo-desktop:~$ sudo blkid

/dev/sda1: UUID="1b3bf77f-702f-45fc-831b-404daba90305" TYPE="ext4" 
/dev/sda5: UUID="387dd97f-93e1-4edb-a9ef-8ab4aa5c4a13" TYPE="ext4" 
/dev/sda6: UUID="05482d21-e398-4fd6-882c-1ecab0c146f3" TYPE="swap" 
/dev/sdf1: LABEL="New Volume" UUID="30f3f69c-5738-49ce-bed0-0d49cbecc31c" TYPE="ext4" 

Thank you.

---

### Post by mikodo on 2011-10-29
forget it. 

I'll never get through this alone

---

### Post by mikodo on 2011-10-29
I received help @#ubuntu IRC.

Thanks.

---

