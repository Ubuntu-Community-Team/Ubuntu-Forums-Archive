---
title: "[SOLVED] Unable to write mmap - msync (28 No space left on device)"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by hundred1906 on 2008-06-30
Ubuntu 8.04 LTS. I am out of disk space and get the following error from Synaptic. This is probably caused by trying to install MythTV - which I gave up on and removed - though there are still traces left on the system.

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I am trying to use Synaptic to delete old versions and review the installed applications for deletion but cannot get beyond the error report box, with the text above, which comes up soon after Synaptic start.

I have run "sudo apt-get clean" with no discernible result.
The same error as above comes up (as I recall) with "sudo apt-get autoclean"

How do I get passed this point. Using the terminal to clear files seems difficult due to the risks involved and the various permissions barriers to be overcome.

---

### Post by plucky on 2008-06-30
From a terminal, post the output of ```
df -h
sudo fdisk -l
```  That is Lowercase L not a 1

---

### Post by onetb on 2008-07-01
Having the same error.  Started when I tried to do updates last night and the samba update failed.   I know that I am not using all my HD space.

df -h outputs:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.4G  7.4G     0 100% /
varrun                375M  232K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M   44K  375M   1% /dev
devshm                375M   12K  375M   1% /dev/shm
lrm                   375M   38M  338M  10% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              65G   29G   33G  47% /home
overflow              1.0M  1.0M     0 100% /tmp
gvfs-fuse-daemon      7.4G  7.4G     0 100% /home/csims/.gvfs

```
and sudo fdisk -l gives:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b637f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1155     1461915   82  Linux swap / Solaris
/dev/sda3            1156        9729    68870655   83  Linux

```
Thanks

EDIT:
Thought I should also note the errors I get when trying to repair dependencies from shell.
When I run either "sudo apt-get -f install" or "sudo apt-get update", I get:
```
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
```

---

### Post by plucky on 2008-07-01
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.4G  7.4G     0 100% /



That is your problem,your root partition is full.What have you been installing on there? My root partition uses 3.5G so something is filling it up.

To gain some space ```
sudo apt-get clean
``` will clear out your synaptic application packages.

Do you have some log files growing out of hand or a backup job pointing at the incorrect folder?

Try this command to find any large files in your root directory ```
sudo find / -type f -size +100000k
```

Good Luck

---

### Post by hundred1906 on 2008-07-01
This is what I get from the terminal:

trevor@Linux-Antec:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.6G  4.6G     0 100% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M   40K  506M   1% /dev/shm
lrm                   506M   38M  469M   8% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb4              14G  600M   13G   5% /home
/dev/sdb2             134G   74G   60G  56% /media/sdb2
overflow              1.0M  424K  600K  42% /tmp
trevor@Linux-Antec:~$ sudo fdisk -l
[sudo] password for trevor: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39ee39ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2609    20956761    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x333eed9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         608     4883728+  83  Linux
/dev/sdb2            2551       19929   139596817+   7  HPFS/NTFS
/dev/sdb3             609         790     1461915   82  Linux swap / Solaris
/dev/sdb4             791        2550    14137200   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c90dcfd

Disk /dev/sdc doesn't contain a valid partition table
trevor@Linux-Antec:~$ 

(NB: I think sdc is a drive I use under windows.)

I knew the root partition to be full. The problem for a newbie is knowing what and how to delete. When I used "sudo find / -type f -size +100000k" I got no report for sdb1 but on reducing the searchsize criteria I did find under PROC four Mythtv log files. I deleted these manually and recovered over 50% of the space in my 4.6G root.

How MythTV can claim that much space when I have not been able to use it I do not know and I am suprised it was still left there when I deleted the application.

Ditto I see that MySQL (which arrived with MythTV) also has log files left on the system but I cannot delete these - apparantly I am not the owner. Just a partial listing is below, I have left out the reports for multiple files on other drives:

/media/sdb2/Video edits/MOV files/AVI files/Vid 107.avi
/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/resource0
/proc/kcore
find: /proc/7064/task/7064/fdinfo/4: No such file or directory
find: /proc/7064/fdinfo/4: No such file or directory
/boot/initrd.img-2.6.24-16-generic
/boot/initrd.img-2.6.24-16-generic.bak
/var/cache/apt/srcpkgcache.bin
/var/cache/apt/pkgcache.bin
/var/lib/mysql/ib_logfile1
/var/lib/mysql/ibdata1
/var/lib/mysql/ib_logfile0
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
trevor@Linux-Antec:~$

---

