---
title: "Installed both 11.10  (32 bit) &amp; 12.04 (64 bit) with WUBI"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by GxEnomics on 2012-07-01
I already had Ubuntu 11.10 installed, via WUBI, on a dual boot XP laptop. Today I decided to install the 64-bit version of 12.04 whilst still keeping the 32-bit 11.10 version active.  I successfully installed 12.04 with WUBI by changing the 11.10 "ubuntu" directory name. To my surprise this worked and I can start either 11.10 or 12.04 by simply going back to XP and changing the "ubuntu" directory name of one of  the versions.

This outcome seems too good to be true so I thought I'd better check whether what I've done is advisable and what, if any, problems might I encounter trying to run two version of Ubuntu in this way. Also, why did the 11.10 install use ~9gig in a 25gig partition while the 12.04 install used only ~3gig in a separate partition?
 

 Cheers, Greg

---

### Post by sudodus on 2012-07-01
> **GxEnomics said:**
> I already had Ubuntu 11.10 installed, via WUBI, on a dual boot XP laptop. Today I decided to install the 64-bit version of 12.04 whilst still keeping the 32-bit 11.10 version active.  I successfully installed 12.04 with WUBI by changing the 11.10 "ubuntu" directory name. To my surprise this worked and I can start either 11.10 or 12.04 by simply going back to XP and changing the "ubuntu" directory name of one of  the versions.

This outcome seems too good to be true so I thought I'd better check whether what I've done is advisable and what, if any, problems might I encounter trying to run two version of Ubuntu in this way.

I think it can work like that (with Wubi) without problems. But when you are convinced that you want to use Ubuntu, I suggest that you install it on its own partitions, because of better stability.
> 
Also, why did the 11.10 install use ~9gig in a 25gig partition while the 12.04 install used only ~3gig in a separate partition?
 
Cheers, Greg

I guess you have added software and personal files to the 11.10 version while you have been using it.

---

### Post by GxEnomics on 2012-07-01
> **GxEnomics said:**
>  Also, why did the 11.10 install use ~9gig in a 25gig partition while the 12.04 install used only ~3gig in a separate partition?
 

I haven't installed any additional software in the 11.10 version.

 I just re-checked the previously quoted installation sizes and there is only 9 gig left in the 11.10 partition, hence  ~15gig is now used while only 3 gig is used in the 12.04 partition. The 11.10 install took up ~9gig prior to the installation of 12.04, so does this mean that 6 gig of the 12.04 installation now resides in the 11.10 partition?

Cheers, Greg

---

### Post by sudodus on 2012-07-02
I don't understand. Please boot the two Ubuntu installations, and from each of them post the output of the following commands:

```
sudo fdisk -lu
```
and
```
df
```

---

### Post by GxEnomics on 2012-07-02
> **sudodus said:**
> I don't understand. Please boot the two Ubuntu installations, and from each of them post the output of the following commands:

```
sudo fdisk -lu
```and
```
df
```

11.10 installation:

   [FONT=Courier New]Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  de  Dell Utility
/dev/sda2   *      192780   125194544    62500882+   7  HPFS/NTFS/exFAT
/dev/sda3       125194545   207109979    40957717+   7  HPFS/NTFS/exFAT
/dev/sda4       207110041   312576704    52733332    f  W95 Ext'd (LBA)
/dev/sda5       207110043   258309134    25599546    7  HPFS/NTFS/exFAT
/dev/sda6       258309198   312576704    27133753+   7  HPFS/NTFS/exFAT

Filesystem           1K-blocks      Used Available Use% Mounted on[/FONT] [FONT=Courier New]
/dev/loop0            14860672   4011872  10093908  29% /
udev                   1023304         4   1023300   1% /dev
tmpfs                   412128       840    411288   1% /run
none                      5120         0      5120   0% /run/lock
none                   1030316       264   1030052   1% /run/shm
/dev/sda5             25599544  16141588   9457956  64% /host[/FONT]

I'll post the 12.04 details in a few minutes. Thanks for your help.

---

### Post by GxEnomics on 2012-07-02
> **sudodus said:**
> I don't understand. Please boot the two Ubuntu installations, and from each of them post the output of the following commands:

```
sudo fdisk -lu
```and
```
df
```

12.04 installation:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  de  Dell Utility
/dev/sda2   *      192780   125194544    62500882+   7  HPFS/NTFS/exFAT
/dev/sda3       125194545   207109979    40957717+   7  HPFS/NTFS/exFAT
/dev/sda4       207110041   312576704    52733332    f  W95 Ext'd (LBA)
/dev/sda5       207110043   258309134    25599546    7  HPFS/NTFS/exFAT
/dev/sda6       258309198   312576704    27133753+   7  HPFS/NTFS/exFAT

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/loop0      13629786 2182777  11447009  17% /
udev             1016176       4   1016172   1% /dev
tmpfs             409984     852    409132   1% /run
none                5120       0      5120   0% /run/lock
none             1024960     152   1024808   1% /run/shm
/dev/sda6       27133752 3390992  23742760  13% /host

Drive details from XP
                                                Total size (GB)                      Free (GB)
C:                                                     59.6                                         23.6
D:                                                     39.0                                         29.6
X: (11.10 installation)                 24.4                                        9.01
Y: (12.04 installation)                 25.8                                        22.6

Cheers, Greg

---

### Post by sudodus on 2012-07-02
I edited your output and added some comments (after #) to make it easier to understand.

```
11.10 installation:
 
 Device   Boot   Start       End    Blocks Id System
 /dev/sda1          63    192779    96358+ de Dell Utility
 /dev/sda2 *    192780 125194544 62500882+ 7  HPFS/NTFS/exFAT
 /dev/sda3   125194545 207109979 40957717+ 7  HPFS/NTFS/exFAT
 /dev/sda4   207110041 312576704 52733332  f  W95 Ext'd (LBA)
 /dev/sda5   207110043 258309134 25599546  7  HPFS/NTFS/exFAT
 /dev/sda6   258309198 312576704 27133753+ 7  HPFS/NTFS/exFAT
 
 Filesystem 1K-blocks     Used Available Use% Mounted on 
 [COLOR="red"]/dev/loop0  14860672  4011872  10093908  29% /         # root file system[/COLOR]
 udev         1023304        4   1023300   1% /dev
 tmpfs         412128      840    411288   1% /run
 none            5120        0      5120   0% /run/lock
 none         1030316      264   1030052   1% /run/shm
 /dev/sda5   25599544 16141588   9457956  64% /host

12.04 installation:
 
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0xc0000000
 
 Device Boot     Start       End    Blocks Id System
 /dev/sda1          63    192779    96358+ de Dell Utility
 /dev/sda2 *    192780 125194544 62500882+ 7  HPFS/NTFS/exFAT
 /dev/sda3   125194545 207109979 40957717+ 7  HPFS/NTFS/exFAT
 /dev/sda4   207110041 312576704 52733332  f  W95 Ext'd (LBA)
 /dev/sda5   207110043 258309134 25599546  7  HPFS/NTFS/exFAT
 /dev/sda6   258309198 312576704 27133753+ 7  HPFS/NTFS/exFAT
 
 Filesystem 1K-blocks    Used Available Use% Mounted on
 [COLOR="red"]/dev/loop0  13629786 2182777  11447009  17% /         # root file system[/COLOR]
 udev         1016176       4   1016172   1% /dev
 tmpfs         409984     852    409132   1% /run
 none            5120       0      5120   0% /run/lock
 none         1024960     152   1024808   1% /run/shm
 /dev/sda6   27133752 3390992  23742760  13% /host
 
 Drive details from XP
 Total size (GB) Free (GB)
 C: 59.6 23.6                       # /dev/sda2 
 D: 39.0 29.6                       # /dev/sda3
 X: (11.10 installation) 24.4 9.01  # /dev/sda5 /host for Ubuntu 11.10
 Y: (12.04 installation) 25.8 22.6  # /dev/sda6 /host for Ubuntu 12.04
 
 Cheers, Greg
```[COLOR="Red"][/COLOR]

```
 Filesystem 1K-blocks    Used Available Use% Mounted on 
/dev/loop0  14860672  4011872  10093908  29% /         # root file system 11.10
/dev/loop0  13629786  2182777  11447009  17% /         # root file system 12.04
```

1. You have the wubi installs on separate logical partitions (X: alias /dev/sda5 and Y: alias /dev/sda6). These are not the same as the file systems for Ubuntu. In a wubi install, the file system resides in a big file in the host partition, and that file is mounted as a loop device.

2a. The root file system for 11.10 is 14860672 kB (approx 15 GB) and 4011872 kB is used (approx 4 GB).

2b. The root file system for 12.04 is 13629786 kB (approx 14 GB) and 2182777 kB is used (approx 2 GB).

3. Check what files you can see in X: and Y: from Windows

4. Mount /dev/sda5 and /dev/sda6 and check what files you can see from Ubuntu!

---

### Post by GxEnomics on 2012-07-02
Thank you Sudodus! 

As an Ubuntu noob everything seems totally foreign but I actually understand what you've just explained to me so that's great help.

I will print off your response and take a closer look at the directories in Ubuntu and Windows.

Cheers, Greg

---

### Post by GxEnomics on 2012-08-09
Is there a way to increase the size of the root file system on a WUBI install?  

I have repartitioned the size of the logical partition Y in Windows (alias /dev/sda6 ; further details are listed in a previous post). This increased the Gb allocation to /host, but it did not allocate more space to /. 

Below is the current output from sudo fdisk -lu and df -h for the 12.04 installation.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  de  Dell Utility
/dev/sda2   *      192780   125194544    62500882+   7  HPFS/NTFS/exFAT
/dev/sda3       125194548   312576704    93691078+   f  W95 Ext'd (LBA)
/dev/sda5       125194611   196876574    35840982    7  HPFS/NTFS/exFAT
/dev/sda6       196876638   312576704    57850033+   7  HPFS/NTFS/exFAT

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       13G   11G  2.4G  82% /
udev            993M  4.0K  993M   1% /dev
tmpfs           401M  868K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  152K 1001M   1% /run/shm
/dev/sda6        56G   14G   42G  25% /host

Cheers, Greg

---

