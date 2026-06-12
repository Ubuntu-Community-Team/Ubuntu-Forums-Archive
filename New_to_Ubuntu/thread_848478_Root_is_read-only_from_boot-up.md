---
title: "Root is read-only from boot-up"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by tipiglen on 2008-07-03
Not quite an absolute newbie, but having problems.

When I open a file browser (nautilus) and go to filesystem, it shows as read-only.  I can't change this, either as sudo or su.  I added a new user, and if I log in as that one, everything is as it should be, but of course with a different home.

Any ideas why this has happened?  I did a new install and everything was ok, but the problem has re-occurred.

code:
[INDENT]
root@ubuntu:/etc# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f62e3f18-02e0-486f-b46a-54a67f105f08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d3dd670e-5b93-4d68-a2de-445b5a31e3ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# hopefully this will get share partition mounted at boot
/dev/sda2 /media/disk-6 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
# same for windows partition mounted at boot
#/dev/sda1 /media/25_02_42_ fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
[/INDENT]

And maybe somebody can tell me how to post code in these messages?

Salaam/Shalom/Shanthi/Dorood/Peace
-ed

---

### Post by tipiglen on 2008-07-03
I also cannot get it to accept a blank cd or dvd for backing up, and it won't recognise most cds or dvds, but will boot from a recovery or system restore disk, and will boot from my 8.04 live cd.

I can get it to read a cd if I mount it as sudo in a terminal.

Puzzled
ed

---

### Post by tipiglen on 2008-07-04
bump!  

Still doing it.  Tried fsck from live cd

```

ubuntu@ubuntu:~$ sudo fsck -rfv /dev/sda3
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  162417 inodes used (9.58%)
    7907 non-contiguous inodes (4.9%)
         # of inodes with ind/dind/tind blocks: 19107/445/0
 3514095 blocks used (51.83%)
       0 bad blocks
       1 large file

  129299 regular files
   15777 directories
      69 character device files
      26 block device files
       2 fifos
     465 links
   17209 symbolic links (16138 fast symbolic links)
      26 sockets
--------
  162873 files
ubuntu@ubuntu:~$ 

```

Will now reboot from hdd and see, but I'm not optimistic.
;-(
ed

---

### Post by chrisccoulson on 2008-07-04
Could you please provide the output of the following please:
```
sudo fdisk -l
ls -l /dev/disk/by-uuid/
```

Thanks

---

### Post by tipiglen on 2008-07-04
Thanks for your reply, Chris.
```

ed@ubuntu:~$ sudo fdisk -l
[sudo] password for ed: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05790579

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4810    38636293+   7  HPFS/NTFS
/dev/sda2            4811        6093    10305697+   b  W95 FAT32
/dev/sda3            6094        9469    27117720   83  Linux
/dev/sda4            9470        9724     2048287+  82  Linux swap / Solaris
ed@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-07-04 17:19 46BF-48D9 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-07-04 17:19 883C7B3E3C7B267A -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-07-04 17:19 d3dd670e-5b93-4d68-a2de-445b5a31e3ec -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-07-04 17:19 f62e3f18-02e0-486f-b46a-54a67f105f08 -> ../../sda3
ed@ubuntu:~$ 
```

Any ideas?
ed

---

### Post by chrisccoulson on 2008-07-06
After re-reading your original description, I'm not sure I fully understand your problem. Are you saying that this only happens with one user? If you are, then this is likely to be a permissions issue as opposed to the disk being read-only.

Could you please take me through the steps to reproduce your problem (be specific, ie - specify locations in the file system and error messages that appear)

Thank you for your patience.

---

### Post by caljohnsmith on 2008-07-06
EDITED: Sorry, I misread the original question when I first answered. I don't have anything to add, but since I can't delete my post, I wish you best of luck in sorting it out. :)

---

