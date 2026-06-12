---
title: "Ubuntu 20.04 -- What are &quot;stale online ext4 metadata check snapshots&quot;"
date: 2023-04-11
forum: New to Ubuntu
---

### Post by bhubunt on 2023-04-11
Hi, 
I've gotten some great suggestions on this forum so far, so I hope you won't mind if I ask yet another question about a code line that I found today in the system log of my Lenovo x230i with an Ubuntu 20.04 OS, desktop -- no server. 

I have not come across this particular code line before and would appreciate it if someone could explain what the following line means

```
 Starting Remove Stale Online ext4 Metadata Check Snapshots 
```

I have come across this line in other people's logs posted online, but no one seems to have broken down what 1/ the function is of this removal, 2/ what exactly is being removed and 3/ why. 

Also, very importantly, 4/ what am I to understand by the word *online* in this code line? 

The sender of the code line was systemd.

Anyone care to explain this ? Thanks.

---

### Post by #&amp;thj^% on 2023-04-11
The sender of the code line was systemd. (indeed it was)
Do you have problems?
```
 systemctl status -o short-precise e2scrub_reap.service
&#9675; e2scrub_reap.service - Remove Stale Online ext4 Metadata Check Snapshots
     Loaded: loaded (/lib/systemd/system/e2scrub_reap.service; enabled; preset:>
     Active: inactive (dead) since Tue 2023-04-11 07:06:45 MDT; 4h 18min ago
       Docs: man:e2scrub_all(8)
   Main PID: 2193 (code=exited, status=0/SUCCESS)
        CPU: 14ms

Apr 11 07:06:45.571086 me-Lenovo-Legion-5-15ARH05 systemd[1]: Starting e2scrub_>
Apr 11 07:06:45.648801 me-Lenovo-Legion-5-15ARH05 systemd[1]: e2scrub_reap.serv>
Apr 11 07:06:45.649127 me-Lenovo-Legion-5-15ARH05 systemd[1]: Finished e2scrub_>

```
and:
```
time e2scrub_all -A -r 
e2scrub_all must be run as root

real	0m0.013s
user	0m0.000s
sys	0m0.004s

```
FWIW:  e2scrub is tied to lvm
My thoughts on the Online question is that it is available to the system.

---

### Post by bhubunt on 2023-04-11
> **1fallen said:**
> 
Do you have problems?


Yes, I have problems as I want to understand what is going on.

Firstly, could you (or someone else) first help me understand why I have LVM on my laptop, with an Ubuntu 20.04 desktop installation, since I did not activate LVM?

Most of the sites I googled discuss LVM for Ubuntu *Server* installation as on this site: [https://packetpushers.net/ubuntu-extend-your-default-lvm-space/](https://packetpushers.net/ubuntu-extend-your-default-lvm-space/)

The one example I found for using LVM for a desktop installation makes it clear that it is a multi-pronged process, involving a number of commands that need to be entered into the terminal, none of which I did (see [https://askubuntu.com/questions/1362766/install-ubuntu-20-04-desktop-with-separate-lvm-partitions-on-uefi-bios-hardware](https://askubuntu.com/questions/1362766/install-ubuntu-20-04-desktop-with-separate-lvm-partitions-on-uefi-bios-hardware))

True?

Second, I'd still like to know what "stale online ext4 metadata check snapshots" are and what *online* means here.

---

### Post by Holger_Gehrke on 2023-04-11
e2scrub is basically a tool for finding file system corruption in ext[234] which can run while the storage is mounted and in use - which is what is meant by the word 'online' in this context. It only finds corruption but doesn't even try to fix it - that would be too risky to try while the system is using the file system. You still need to run e2fsck if e2scrub has found problems. To perform this minor miracle, it uses snapshots in LVM to 'freeze' the state of the file system in time. The systemd service e2scrub_reap removes old stale snapshots at boot. It removes them since they are a waste of storage. It seems this service is installed by default, even on systems which aren't using LVM. Since there are no snapshots to clean up, it just exits with a status of '0' aka 'success'.

Holger

---

### Post by bhubunt on 2023-04-11
> **Holger_Gehrke said:**
> e2scrub is basically a tool for finding file system corruption in ext[234] which can run while the storage is mounted and in use - which is what is meant by the word 'online' in this context. It only finds corruption but doesn't even try to fix it - that would be too risky to try while the system is using the file system. You still need to run e2fsck if e2scrub has found problems. To perform this minor miracle, it uses snapshots in LVM to 'freeze' the state of the file system in time. The systemd service e2scrub_reap removes old stale snapshots at boot. It removes them since they are a waste of storage. It seems this service is installed by default, even on systems which aren't using LVM. Since there are no snapshots to clean up, it just exits with a status of '0' aka 'success'.

Holger

OK, thanks for the detailed explanation.

Is there a terminal command to check if a system has LVM?

---

### Post by #&amp;thj^% on 2023-04-11
> **bhubunt said:**
> OK, thanks for the detailed explanation.

Is there a terminal command to check if a system has LVM?

There is no need for that see the man page:
```
E2SCRUB(8)                  System Manager's Manual                 E2SCRUB(8)

NAME
       e2scrub_all - check all mounted ext[234] file systems for errors.

SYNOPSIS
       e2scrub_all [OPTION]

DESCRIPTION
     [B][U]  Searches  the  system  for  all LVM logical volumes containing an ext2,
       ext3, or ext4 file system, and checks them for problems.  [/U][/B]The  checking
       is  performed by invoking the e2scrub tool, which will look for corrup&#8208;
       tions.  Corrupt file systems will be tagged as having  errors  so  that
       fsck  will  be invoked before the next mount.  If no errors are encoun&#8208;
       tered, fstrim will be called on the file system if it is mounted.   See
       the  e2scrub manual page for more information about how the checking is
       performed.


```
EDIT: Ok you win: by using the "lvdisplay" command. If you have any logical volumes they will appear as such.

---

### Post by bhubunt on 2023-04-11
> **1fallen said:**
> There is no need for that see the man page:
```

     [B][U]  Searches  the  system  for  all LVM logical volumes containing an ext2,
       ext3, or ext4 file system, and checks them for problems.  [/U][/B]


```

OK -- but this section from the man page seems to contradict what Holger just wrote: Holger said the scrub tool is active without LVM. Yet, this quote from the man page suggests that the scrub tool does search LVM logical volumes, so that it presupposes LVM...

Also, my question from the previous post is still different: I'd like to know if there is a command one can enter into the terminal to see if LVM has been applied to the system. If so, what is that command?

---

### Post by #&amp;thj^% on 2023-04-11
> **bhubunt said:**
> OK -- but this section from the man page seems to contradict what Holger just wrote: Holger said the scrub tool is active without LVM. Yet, this quote from the man page suggests that the scrub tool does search LVM logical systems, so that it presupposes LVM...
maybe reread his post  Holger seldom offers bad info.
> **bhubunt said:**
> 
Also, my question from the previous post is still different: I'd like to know if there is a command one can enter into the terminal to see if LVM has been applied to the system. If so, what is that command?

I just gave it to you in my previous post " "lvdisplay" is good tool for those who do use LVM:
mine is:
```
lvm formats
  WARNING: Running as a non-root user. Functionality may be unavailable.
  lvm2

```
more:
```
>> lvm devtypes
  WARNING: Running as a non-root user. Functionality may be unavailable.
  DevType       MaxParts Description                               
  VxDMP               16 Veritas Dynamic Multipathing              
  aoe                 16 ATA over Ethernet                         
  ataraid             16 ATA Raid                                  
  bcache               1 bcache block device cache                 
  blkext               1 Extended device partitions                
  cciss               16 Compaq CCISS array                        
  dac960               8 DAC960                                    
  dasd                 4 DASD disk (IBM S/390, zSeries)            
  device-mapper        1 Mapped device                             
  drbd                16 Distributed Replicated Block Device (DRBD)
  emcpower            16 EMC Powerpath                             
  fio                 16 Fusion IO                                 
  gnbd                 1 Network block device                      
  i2o_block           16 i2o Block Disk                            
  ida                 16 Compaq SMART2                             
  ide                 64 IDE disk                                  
  iseries/vd           8 iSeries disks                             
  loop                 1 Loop device                               
  md                   1 Multiple Disk (MD/SoftRAID)               
  mdp                  1 Partitionable MD                          
  mmc                 16 MMC block device                          
  mtip32xx            16 Micron PCIe SSD                           
  nbd                 16 Network Block Device                      
  nvme                64 NVM Express                               
  power2              16 EMC Powerpath                             
  ps3disk             16 PlayStation 3 internal disk               
  ramdisk              1 RAM disk                                  
  rbd                 16 Ceph rados object as a Linux block device 
  scm                  8 Storage Class Memory (IBM S/390)          
  sd                  16 SCSI disk                                 
  skd                 16 STEC                                      
  ubd                 16 User-mode virtual block device            
  vdisk                8 SUN's LDOM virtual block device           
  virtblk              8 VirtIO disk                               
  vtms                16 Violin Memory                             
  xvd                 16 Xen virtual block device                  
  zvol                16 ZFS Zvols 
```
Your compare to mine will help, I hope. :)

---

### Post by bhubunt on 2023-04-11
OK, super. I'll enter those commands tomorrow.

I didn't mean to question Holger's knowledge by any means! 

Holger's given superb explanations in other threads of mine.

 Rather, it seemed that the man page is incomplete as it does not mention that the scrub tool can also operate on a system without LVM. Perhaps that's mentioned somewhere else in other Linux manuals --not sure.

---

### Post by Holger_Gehrke on 2023-04-11
e2scrub and e2scrub_all are part of the e2fsprogs package. They only make sense if you're using ext[234] file systems inside the Logical Volume Manager but they are installed nonetheless. If it gets called without LVM present it just exits with an exit code of 0 without doing anything. The systemd service is installed in a one size fits all manner - it doesn't do any harm if run without LVM because it just starts and exits without doing anything. The message you find in your log is produced by systemd, not by e2fsscrub which keeps to the old UNIX idea of 'no news is good news' and does no output if it succeeded (and in a way it does succeed - there are no stale snapshots on the system after it has run, since there are no snapshots without LVM ...). If you look in /usr/lib/systemd/system/e2scrub_reap.service you'll find the message - without the 'Starting ' at its beginning - is actually the description of the service.

Holger

---

### Post by bhubunt on 2023-04-12
Here is what I get when I type in sudo lvdisplay

 The LV status is available. 

Can someone unpack what you see? 

What does current LE mean? 

I take it that the swap space is automatically part of the Ubuntu installation. See [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Do I conclude from the code below that LVM is also automatically part of the Ubuntu 20.04 installation and can then be used by entering specific commands  -- or not? 

```

--- Logical volume ---
  LV Path                /dev/vgubuntu/root
  LV Name                root
  VG Name                vgubuntu
  LV UUID                VYh3ay-F9Ab-tb8G-2Oak-8a6Q-Tta5-dZTrWv
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2023-03-31 12:46:27 +0200
  LV Status              available
  # open                 1
  LV Size                462,84 GiB
  Current LE             118488
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vgubuntu/swap_1
  LV Name                swap_1
  VG Name                vgubuntu
  LV UUID                KZAhTF-dCsA-Pbb1-r6V0-RJPH-j8d0-0Ptrcc
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2023-03-31 12:46:27 +0200
  LV Status              available
  # open                 2
  LV Size                976,00 MiB
  Current LE             244
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2 
```

---

### Post by maglin2 on 2023-04-12
Did you select encryption during installation?
(Edit - Long time since I installed 20.04, but looking back at the guide it suggests you have to select LVM to be offered Encryption, not the other way around, and you said in #3 you didn't activate LVM).

---

### Post by #&amp;thj^% on 2023-04-12
> **maglin2 said:**
> Did you select encryption during installation?
+1

> What does current LE mean? 
You almost had me on that one, had to have a second cup of coffee for that one.:)
Meaning:"logical extent (LE)", Each logical volume is split into chunks of data, known as logical extents. The extent size is the same for all logical volumes in the volume group. 
Or as (PE) physical extent (PE)
if you use certain back-up tools LMV could be pulled in.
> Do I conclude from the code below that LVM is also automatically part of the Ubuntu 20.04 installation and can then be used by entering specific commands -- or not?

I'm not certain on this one, but as said>>certain back-up tools LMV could be pulled in.
EDIT: Just confirmed, depending on environments on your initial Install, it looks like it is used.
```
Package: lvm2
Version: 2.03.16-1ubuntu1
Priority: optional
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LVM Team <team+lvm@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,162 kB
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: libaio1 (>= 0.3.93), libblkid1 (>= 2.24.2), libc6 (>= 2.34), libdevmapper-event1.02.1 (>= 2:1.02.74), libedit2 (>= 2.11-20080614-0), libselinux1 (>= 3.1~), libsystemd0 (>= 233), libudev1 (>= 183), systemd | systemd-tmpfiles, lsb-base, dmsetup (>= 2:1.02.185-1ubuntu1~), dmeventd (>= 2:1.02.185-1ubuntu1~)
Recommends: thin-provisioning-tools
Homepage: https://sourceware.org/lvm2/
Task: server-minimal, cloud-image, ubuntu-live, server, ubuntu-server-raspi, kubuntu-live, xubuntu-live, lubuntu-live, ubuntustudio-dvd-live, ubuntukylin-live, ubuntu-mate-live, ubuntu-budgie-live, ubuntu-unity-live, edubuntu-dvd-live, edubuntu-server-raspi
Download-Size: 1,187 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
Description: Linux Logical Volume Manager
 This is LVM2, the rewrite of The Linux Logical Volume Manager.  LVM
 supports enterprise level volume management of disk and disk subsystems
 by grouping arbitrary disks into volume groups. The total capacity of
 volume groups can be allocated to logical volumes, which are accessed as
 regular block devices.

N: There is 1 additional record. Please use the '-a' switch to see it

```
And we know already I use it:
```
apt policy lvm2
lvm2:
  Installed: 2.03.16-1ubuntu1
  Candidate: 2.03.16-1ubuntu1
  Version table:
 *** 2.03.16-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
     2.03.11-2.1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages


```

---

### Post by bhubunt on 2023-04-12
> **maglin2 said:**
> Did you select encryption during installation?
(Edit - Long time since I installed 20.04, but looking back at the guide it suggests you have to select LVM to be offered Encryption, not the other way around, and you said in #3 you didn't activate LVM).

Yes, I did. Problem solved.

---

### Post by bhubunt on 2023-04-12
> **1fallen said:**
> +1


You almost had me on that one, had to have a second cup of coffee for that one.:)


Yes, indeed, I selected encryption  --

That also explains why 
e2scrub_reap.service 

is on my system, getting rid of those pesky stale online ext4 metadata check snapshots 
(what a mouthful)

---

### Post by #&amp;thj^% on 2023-04-12
> **bhubunt said:**
> 
(what a mouthful):lolflag::lolflag:

---

