---
title: "Error: no such partition. grub rescue &gt;"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by medman826 on 2012-06-30
I have a similar problem. I am currently running a dual boot setup with ubuntu on my macbook pro 8,2. The partition scheme is as follows:

1: EFI
2: Macintosh HD
3: Lion recovery
4: linux swap drive
5: Linux filesystem

Here is the output from diskutil list:

[B]/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS HD                      465.0 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:                 Linux Swap                         9.2 GB     disk0s4
   5: 0FC63DAF-8483-4772-8E79-3D69D8477DE4               20.0 GB    disk0s5[/B]

Here is the output from gdisk:


[B]Disk /dev/disk0: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003AD5-6824-0000-2112-0000DD520000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 9831517 sectors (4.7 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       908612759   433.1 GiB   AF00  Customer
   3       908612760       909882295   619.9 MiB   AB00  Recovery HD
   4       919713792       937711615   8.6 GiB     8200  SWAP
   5       937711616       976773119   18.6 GiB    8300  UBUNTU[/B]

The problem is that I get the same message when I boot, and clearly my partition scheme is messed up. Fortunately I am still able to boot into mac just as before.

Is there any way to fix this?

---

### Post by oldos2er on 2012-06-30
Post moved to its own thread.

---

