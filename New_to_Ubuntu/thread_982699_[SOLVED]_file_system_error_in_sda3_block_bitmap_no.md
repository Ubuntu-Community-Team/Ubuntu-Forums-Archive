---
title: "[SOLVED] file system error in sda3 block bitmap not in group"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-15
I'm in a LiveCD session. I want to run fsck against /sda3 as described at boot time (where OS didn't boot to the splash screen)

e2fsck -b 32768

ubuntu@ubuntu:/$ dmesg | tail
[  383.459768] EXT3 FS on sda1, internal journal
[  383.459777] EXT3-fs: mounted filesystem with ordered data mode.
[  383.527501] usb 4-2: new high speed USB device using ehci_hcd and address 6
[  388.533871] usb 4-2: device descriptor read/8, error -110
[  391.982501] EXT2-fs error (device sda3): ext2_check_descriptors: Block bitmap for group 1280 not in group (block 0)!
[  391.982515] EXT2-fs: group descriptors corrupted!
[  393.639942] usb 4-2: device descriptor read/8, error -110
[  393.855299] usb 4-2: new high speed USB device using ehci_hcd and address 7
[  398.861684] usb 4-2: device descriptor read/8, error -110
[  403.967763] usb 4-2: device descriptor read/8, error -110

---

### Post by cdtech on 2008-11-15
Lets see from the terminal:
```
sudo fdisk -l
```

---

### Post by cdtech on 2008-11-15
Never mind, just boot the Live CD and run:
```
sudo e2fsck -C0 -p -f -v /dev/sda3
```

**-C0** This option causes e2fsck to write completion information to the specified file descriptor

**-p**  Automatically repair ("preen") the  file  system.

**-f**  Force checking even if the file system seems clean.

**-v**  Verbose mode.

---

### Post by Mark_in_Hollywood on 2008-11-15
> **cdtech said:**
> Never mind, just boot the Live CD and run:
```
sudo e2fsck -C0 -p -f -v /dev/sda3
```

**-C0** This option causes e2fsck to write completion information to the specified file descriptor

**-p**  Automatically repair ("preen") the  file  system.

**-f**  Force checking even if the file system seems clean.

**-v**  Verbose mode.

ran the line and it said it won't work with -p, so I removed it and then was asked if I wanted to correct line after line, an example of which is below:

Inode 3000670 has illegal block(s).  Clear<y>? yes

Illegal block #0 (575160731) in inode 3000670.  CLEARED.
Illegal block #1 (2585948017) in inode 3000670.  CLEARED.
Illegal block #2 (1516745546) in inode 3000670.  CLEARED.
Illegal block #3 (1598663520) in inode 3000670.  CLEARED.
Illegal block #4 (2591654889) in inode 3000670.  CLEARED.
Illegal block #5 (1571405617) in inode 3000670.  CLEARED.
Illegal block #6 (289608247) in inode 3000670.  CLEARED.
Illegal block #7 (2135957690) in inode 3000670.  CLEARED.
Illegal block #8 (2996230712) in inode 3000670.  CLEARED.
Illegal block #9 (4147152124) in inode 3000670.  CLEARED.
Illegal block #10 (2940980545) in inode 3000670.  CLEARED.
Too many illegal blocks in inode 3000670.
Clear inode<y>? yes

Inode 3000636 has INDEX_FL flag set but is not a directory.
Clear HTree index<y>? yes

Inode 3000636, i_size is 2710070727967490594, should be 0.  Fix<y>? yes

Inode 3000636, i_blocks is 367695678, should be 0.  Fix<y>?

so for 30 minutes I held the 'y' key down and got up to 3000000 blocks. Do you know how many blocks there are? Is there a better way to do this? It's midnight on the Pacific Coast, I'm shutting the 'puter down for the night. I'll be back Saturday. Thanks.

---

### Post by Mark_in_Hollywood on 2008-11-17
I've done a clean install.

---

### Post by bgiddins on 2009-01-02
> **Mark_in_Hollywood said:**
> 
so for 30 minutes I held the 'y' key down

Use the -y option - default answers "yes" to all questions.

---

### Post by cholericfun on 2009-02-10
Hi, i got a similar problem.
was hoping 
sudo e2fsck -C0 -p -f -v /dev/sda3
would work - however the "reply" is
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

well...there is no /dev/sda3 (i'm in the Live CD by the way)
but
ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd59bd59b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3928    31551628+   7  HPFS/NTFS
/dev/sda2            3929       10302    51199155    7  HPFS/NTFS
/dev/sda3           10814       19457    69432930   83  Linux
/dev/sda4           10303       10813     4104607+  82  Linux swap / Solaris

Partition table entries are not in disk order


any quickfix?

---

