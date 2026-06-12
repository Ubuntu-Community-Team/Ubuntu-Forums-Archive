---
title: "No view of hard drives"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by shawfield on 2008-09-23
Ubuntu is great & I have had no big problems so far.

However, why is it that Ubuntu doesnt recognise the other partitions on my hard drive ?

I wanted to copy my music from what was my c: drive in windows ( its still there in its own partition ) over the network.

But Ubuntu only shows the partition that Ubuntu is installed upon. It does not display any details of the other ( original ) partition. This is the same whether I have properly installed Ubuntu, or whether I am using a live CD.

Is there a different application to use to 'see' those files on the other partition ? I am using the 'places' menu on the panel & clicking on 'computer'.

Thanks
Mike

---

### Post by tangibleorange on 2008-09-23
> **shawfield said:**
> Ubuntu is great & I have had no big problems so far.

However, why is it that Ubuntu doesnt recognise the other partitions on my hard drive ?

I wanted to copy my music from what was my c: drive in windows ( its still there in its own partition ) over the network.

But Ubuntu only shows the partition that Ubuntu is installed upon. It does not display any details of the other ( original ) partition. This is the same whether I have properly installed Ubuntu, or whether I am using a live CD.

Is there a different application to use to 'see' those files on the other partition ? I am using the 'places' menu on the panel & clicking on 'computer'.

Thanks
Mike

could you post the output of:

```
sudo fdisk -l
```

---

### Post by pastalavista on 2008-09-23
Check System>Administration>Synaptic Package Manager and install (if they aren't already) ntfs-3g, ntfs-config and optionally, ntfsprogs. Then reboot and see if it helped.

---

### Post by Circus-Killer on 2008-09-23
its also important to remember that linux doesn't have a c: or d: etc.

instead, partitions and drives are mounted to an empty directory. for example if i wanted to mount the partition labeled /dev/sda2, i would mount it to something like /media/sda or whatever. point being that you access a drive or partition by mounting it to a directory and then go into that directory to view the drive/partition contents.

---

### Post by shawfield on 2008-09-23
root@mike-desktop:/home/mike# sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
root@mike-desktop:/home/mike#

---

### Post by tangibleorange on 2008-09-23
> **shawfield said:**
> root@mike-desktop:/home/mike# sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
root@mike-desktop:/home/mike#

sorry that's a lower case L - l
not a 1. my bad, i should have cleared that up...

---

### Post by shawfield on 2008-09-23
Sorry - wrong parameter !

This is better...

root@mike-desktop:/home/mike# sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
root@mike-desktop:/home/mike#

---

### Post by shawfield on 2008-09-23
oops...the curse of Ctrl-C in Linux strikes again. I can never get that to work...

root@mike-desktop:/home/mike# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45b32571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1019     8185086   83  Linux
/dev/sda2            1020       19457   148103235    5  Extended
/dev/sda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda6            1529        3293    14177331   83  Linux
/dev/sda7            3294       19104   127001826   83  Linux
/dev/sda8           19105       19457     2835441   82  Linux swap / Solaris
root@mike-desktop:/home/mike#

---

### Post by Orange_and_Green on 2008-09-23
Hello Mike :)

I hate to break such news to you but... I can't see any Windows partitions in there... You obviously did a manual partitioning when you installed Ubuntu the first time... are you sure you did not delete/overwrite the Windows partition?

You are talking about network... Is the C: partition you are talking about supposed to reside on the same computer you are using for Ubuntu, or are we talking about two different computers on a LAN?

---

### Post by shawfield on 2008-09-23
Its all a bit odd.

I removed the drive & connected via an enclosure to my Acer One ( Linpus Linux Lite ).

That reports a volume called 'x' ( which, when I viewed it on my Ubuntu machine, I presumed was a Linux directory ). This contains all of the files you'd expect to see on a Windows root directory - autoexec,bat, config.sys etc. My old music directory is there too, but no 'windows' directory. The folder was very 'flaky' under Linpus Lite & kept hanging.

When I put the drive back into my ubuntu machine, it is indeed shown there as 'x', but contains only one file "pagefile.sys" & has 85gb of free space.
No music directory & no autoexec.bat etc etc. 

Curioser & curioser...

---

### Post by tangibleorange on 2008-09-23
> **shawfield said:**
> Its all a bit odd.

I removed the drive & connected via an enclosure to my Acer One ( Linpus Linux Lite ).

That reports a volume called 'x' ( which, when I viewed it on my Ubuntu machine, I presumed was a Linux directory ). This contains all of the files you'd expect to see on a Windows root directory - autoexec,bat, config.sys etc. My old music directory is there too, but no 'windows' directory. The folder was very 'flaky' under Linpus Lite & kept hanging.

When I put the drive back into my ubuntu machine, it is indeed shown there as 'x', but contains only one file "pagefile.sys" & has 85gb of free space.
No music directory & no autoexec.bat etc etc. 

Curioser & curioser...

hmm that's not good. i'd try and pull any files you need off the windows partition any way you can (onto an external hard drive or DVD or USB stick) and then reformat the drive...

---

