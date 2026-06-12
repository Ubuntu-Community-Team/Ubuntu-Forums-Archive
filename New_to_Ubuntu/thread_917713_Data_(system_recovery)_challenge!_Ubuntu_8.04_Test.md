---
title: "Data (system recovery) challenge! Ubuntu 8.04 Testdisk mistake?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Rorke on 2008-09-12
[Half solved: recovered data, reinstalled system]

OK - I think my system is now officially beyond help, but incase someone out there likes a challenge and wants to spend an hour or so coaching me through a recovery, here is what testdisk lists for files in my Linux partition.
By the way, if someone knows of how to make a rescue boot disk, that would be good to know too!
>
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

   L Linux                 3230   2  1 21293 254 63  290198034
Use Right arrow to change directory, q to quit
Directory /

drwxr-xr-x     0     0      4096  9-Sep-2008 19:00 .
drwxr-xr-x     0     0      4096  9-Sep-2008 19:00 ..
drwx------     0     0   1884160 25-Jun-2008 07:27 lost+found
drwxr-xr-x     0     0      4096 22-Apr-2008 18:07 var
lrwsr-Srwx 57095  1170   15065522355205783295 28-Nov-1972 15:51 media
?--sr-sr-t 59869 22457   2236538780790197792 21-Oct-2015 02:14 cdrom
-rwx------  1000  1000     90505  6-Sep-2008 17:04 bin
?---------     0     0         0                   boot
?---------     0     0         0                   home
?---------     0     0         0                   mnt
?---------   118     0   2304501527726129153  1-Jan-1970 00:00 proc
?--xrwSr-t 64442 36612   14890693316174196081 27-May-1943 00:44 root
?--x------ 47647 18512   40794872932755562 19-Feb-1919 16:51 initrd.img
?----w-r-x 52739 20135   1156470803246904651 11-Apr-2015 23:11 vmlinuz
?rwSrws-w- 10987 44131   6940240733269599686 20-Jun-1908 23:56 initrd.img.old
?rw---s-w- 19806 50807   16719720002098219432 11-Aug-2006 19:22 vmlinuz.old
>

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3229 254 63   51889887
 2 E extended LBA          3230   1  1 30400 254 63  436502052
 5 L Linux                 3230   2  1 21293 254 63  290198034
 6 L Linux Swap           28888   1  1 29644 254 63   12161142
 7 L Linux Swap           29645   1  1 30400 254 63   12145077

Results
   * HPFS - NTFS              0   1  1  3229 254 63   51889887
     NTFS, 26 GB / 24 GiB
   D Linux                 3230   2  1 21293 254 63  290198034
     EXT3 Large file Sparse superblock, 148 GB / 138 GiB
   D Linux                 3231   0  1 21294 254 63  290198160
     EXT3 Large file Sparse superblock, 148 GB / 138 GiB
   L Linux Swap           28888   1  1 29644 254 63   12161142
     SWAP2 version 1, 6226 MB / 5938 MiB
   L Linux Swap           29645   1  1 30400 254 63   12145077
     SWAP2 version 1, 6218 MB / 5930 MiB

---

### Post by steve-shinn on 2008-09-12
What exactly are you wanting to recover ?

---

### Post by bumanie on 2008-09-12
[Read this]("http://www.users.bigpond.net.au/hermanzone/p21.html"), it is a step by step guide. As said above, it would help to know what you are trying to recover. Testdisk works well.

---

### Post by Rorke on 2008-09-12
Hi, glad to know someone is out there!
I have most of the irreplaceable stuff (photos) backed up.
I seem to have lost my partition table using GParted but have assigned a wrong one to a previously deleted partition using testdisk.
I know that there is some 30GiB of data in a 138Gib partition, but the partition is not correctly defined.
I am just starting to read the link you sent (thanks :-) I'll see how I go.
Check my previous post for more details on how I got to this sorry place :-(

---

