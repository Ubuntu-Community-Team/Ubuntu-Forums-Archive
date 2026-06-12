---
title: "Shared Data Problem"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by shyamsa on 2011-10-24
Hi,

Currently I installed latest version of ubuntu on my Sony vaio.

I have window7 and ubuntu on it. For accessing the common data I have installed ubuntu on "D:\" and shared the folder completely.

I was able to browse the shared folder from both OS, but when I installed the latest version of ubuntu, I could not see any data on my D:\ drive.

Also I could not see any data from Window7 and Ubuntu.

The space usage remain same, like it show only 5GB is free from current 100GB which I had allocated for Ubuntu OS installation.

How I can get back all the data?

---

### Post by ArgusVision on 2011-10-24
Am I reading correctly that you had data on the D: drive and then installed Ubuntu on that D: drive?

If that is the case, it sounds like you overwrote at least a portion of the data with the Ubuntu OS files.

---

### Post by shyamsa on 2011-10-24
Yes you are correct. But I have use previous version ubuntu  and it was showing all shared data. Now I have upgraded to latest version. I can't see my data.

---

### Post by ArgusVision on 2011-10-24
Was the previous version of Ubuntu installed on the D: drive?

---

### Post by shyamsa on 2011-10-24
Yes, and i was using Window7(installed in C:\) and Ubuntu10.0(installed in D:\) very well before upgrading the ubuntu.

---

### Post by oldfred on 2011-10-24
Ubuntu does not install on a D: drive unless you have used wubi. So is this a wubi install?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by shyamsa on 2011-10-24
No, wubi was not used for installation of Ubuntu.

---

### Post by oldfred on 2011-10-24
From liveCD post this:

sudo fdisk -lu

---

### Post by shyamsa on 2011-10-24
To rephrase my question/problem:

I have not installed ubuntu on D:\, I have installed ubuntu on other partition. I have shared D:\ so that I can access both window and ubuntu data simultaneously.

Hope this will give a more clear view of my problem.

---

### Post by oldfred on 2011-10-24
Post this then:

```
df -H
mount
cat /etc/fstab
```

If you want to read ahead:
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Miljet on 2011-10-24
Once again, please open a terminal and enter the command
```
sudo fdisk -lu
```
and post the results here.

This is so the people who are trying to help you don't have to guess at your configuration.

Thank you.

---

### Post by shyamsa on 2011-10-24
The trace after executing the posted command:


shyam@shyam-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               15G   5.0G   9.1G  36% /
none                   2.0G   721k   2.0G   1% /dev
none                   2.0G   611k   2.0G   1% /dev/shm
none                   2.0G   443k   2.0G   1% /var/run
none                   2.0G      0   2.0G   0% /var/lock
/dev/sda9               11G   242M    11G   3% /boot
/dev/sda8               60G   9.5G    47G  17% /home
/dev/sda7               60G    53G   7.0G  89% /windows/D
shyam@shyam-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda9 on /boot type ext3 (rw,commit=600)
/dev/sda8 on /home type ext3 (rw,user_xattr,commit=600)
/dev/sda7 on /windows/D type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shyam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shyam)
shyam@shyam-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8dbc83c7-5bc4-42ff-9b5b-89cf95d44eee /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
UUID=f3348f6d-90fb-49cb-af0c-085d3055ee91 /boot           ext3    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=73feaf65-ccd9-41ef-acbe-4785f2dcb752 /home           ext3    defaults,user_xattr        0       2
# /windows/D was on /dev/sda7 during installation
UUID=7618-2D63  /windows/D      vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=65f34c57-af09-4d5d-97b9-4bfb6a032aea none            swap    sw              0       0

---

### Post by shyamsa on 2011-10-24
Traces for executing the command sudo fdisk -lu

shyam@shyam-laptop:~$ sudo fdisk -lu
[sudo] password for shyam: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75305d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28391423    14194688   27  Unknown
/dev/sda2   *    28391424    28596223      102400    7  HPFS/NTFS
/dev/sda3        28596224   332214959   151809368    7  HPFS/NTFS
/dev/sda4       332216318   625139711   146461697    5  Extended
/dev/sda5       332216320   361510911    14647296   83  Linux
/dev/sda6       361512960   369324031     3905536   82  Linux swap / Solaris
/dev/sda7       369326080   486510591    58592256    b  W95 FAT32
/dev/sda8       486512640   603697151    58592256   83  Linux
/dev/sda9       603699200   625139711    10720256   83  Linux

---

### Post by oldfred on 2011-10-25
I know spaces in names are an issue, so I do not use them. You are trying to mount as /windows/D which then becomes a path. I would suggest something without the / as the name of the mount point. I use shared.

I stopped using FAT32 for storing data after I lost several large files. FAT cannot store any file over 4GB and has no journal, so chkdsk on a large partition can take ages. It is ok for flash drives that are smaller 4GB or less or other devices that you have to have FAT for compatibility, but otherwise NTFS is much better. You still need to manually run chkdsk every 40 boots or so.

---

### Post by shyamsa on 2011-10-25
Thanks for reply. But how can I get my data back. I have very important document and  don't have any backup. Please suggest.

---

### Post by oldfred on 2011-10-25
Is the partition not there? With its data? 

You should first try chkdsk but on a FAT partition of any size it can take a long time. 

If not otherwise recoverable:

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I have used photorec. It takes a long time as it scans drive for anything that looks like a file. It does not restore filename, just extension. You have to have another device with lots of space as it copies a lot of data to the other device.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

---

### Post by shyamsa on 2011-10-25
I have tried chkdsk on window, but it show error.


[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/) Is this valid for ubuntu 11.04.

---

### Post by oldfred on 2011-10-25
You have to rerun chkdsk until there are no errors as it does not fix them all at once. 

Testdisk & photorec scan drive. You can download from the repository in Ubuntu or Ubuntu liveCD. Many Linux repair CDs include them automatically.

---

### Post by shyamsa on 2011-10-28
It help.. though i cud not recovered all the file.. but i cud manage most of it...thanks..

---

