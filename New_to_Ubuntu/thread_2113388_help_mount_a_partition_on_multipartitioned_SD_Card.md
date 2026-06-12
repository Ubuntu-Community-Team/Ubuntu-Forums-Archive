---
title: "help mount a partition on multipartitioned SD Card"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by paichkash on 2013-02-07
hi
i have 64gb sd card . i used minitools in winxp and made 4 primary partitions .. all are in ext2 format .
now in ubuntu i want to be able to mount them .. what to do ?

```
baldeagle@baldeagle-desktop:~/Desktop/64gb_mounts$ sudo mount -t ext2 /dev/sdb3 ./sdb3_mount
mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


```
baldeagle@baldeagle-desktop:~/Desktop/64gb_mounts$ ls -l /dev/sdb*
brw-rw---- 1 root disk 8, 16 2013-02-07 18:59 /dev/sdb
brw-rw---- 1 root disk 8, 17 2013-02-07 18:59 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2013-02-07 18:59 /dev/sdb2
brw-rw---- 1 root disk 8, 19 2013-02-07 18:59 /dev/sdb3
brw-rw---- 1 root disk 8, 20 2013-02-07 18:59 /dev/sdb4

```


```
baldeagle@baldeagle-desktop:~/Desktop/64gb_mounts$ sudo fdisk /dev/sdb
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

Using /dev/sdb
Command (m for help): p                                                   

Disk /dev/sdb: 67 GB, 67101834240 bytes
255 heads, 63 sectors/track, 8158 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1        2636    21173638   83  Linux
/dev/sdb2            2637        5157    20241900   83  Linux
/dev/sdb3            5158        6696    12353985   83  Linux
/dev/sdb4            6697        8158    11735482   83  Linux

```

---

### Post by Cheesemill on 2013-02-07
I wouldn't trust any Windows software to format ext partitions properly.

Try formatting them again from Ubuntu using...
```
sudo mkfs.ext2 /dev/sdb3
```

---

### Post by paichkash on 2013-02-07
> **Cheesemill said:**
> I wouldn't trust any Windows software to format ext partitions properly.

Try formatting them again from Ubuntu using...
```
sudo mkfs.ext2 /dev[COLOR=Red]**/sd3**[/COLOR]
```
hmm
i was also suspecting the error message bad superblock to mean incorrect formating .. but again i created and formated all the 4 partitions using minitools .. and first one is working flawlessly but rest are not . 

i just fired up gparted and its taking a lot of time to format the sdb2 as ext4 ..  :confused:  is mkfs.ext2 any fast ?

---

### Post by Cheesemill on 2013-02-07
Sorry for the typo earlier, I've corrected my original post.

Gparted uses the mkfs command for formatting so it will take the same amount of time.

---

### Post by paichkash on 2013-02-07
i formated it both ways .. using gparted and the mkfs.ext2/4 options ..  still getting this error


```
baldeagle@baldeagle-desktop:~/Desktop/64gb_mounts$ sudo mount -t ext4 /dev/sdb3 ./sdb3_mount
mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````
baldeagle@baldeagle-desktop:~/Desktop/64gb_mounts$ dmesg | tail
[ 2563.181994] EXT4-fs (sdb2): group descriptors corrupted!
[ 3302.029557] EXT2-fs (sdb4): error: ext2_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 3302.029562] EXT2-fs (sdb4): group descriptors corrupted
[ 3327.654683] EXT4-fs (sdb3): ext4_check_descriptors: Checksum for group 0 failed (57205!=0)
[ 3327.654688] EXT4-fs (sdb3): group descriptors corrupted!
[ 3334.009561] EXT4-fs (sdb2): VFS: Can't find ext4 filesystem
[ 3382.784206] EXT4-fs (sdb3): ext4_check_descriptors: Checksum for group 0 failed (57205!=0)
[ 3382.784210] EXT4-fs (sdb3): group descriptors corrupted!
[ 3397.083960] EXT4-fs (sdb3): ext4_check_descriptors: Checksum for group 0 failed (57205!=0)
[ 3397.083965] EXT4-fs (sdb3): group descriptors corrupted!
```

---

### Post by oldfred on 2013-02-07
You are trying to mount as ext4 but it is ext2?

I have seen that it is better to use ext4 and turn journal off. As ext4 has some other improvements over ext2. 
       sudo tune2fs -O ^has_journal /dev/sdXY # where X is drive & Y is partition

---

### Post by paichkash on 2013-02-09
> **oldfred said:**
> **You are trying to mount as ext4 but it is ext2?**

I have seen that it is better to use ext4 and turn journal off. As ext4 has some other improvements over ext2. 
       sudo tune2fs -O ^has_journal /dev/sdXY # where X is drive & Y is partition

where exactly ?
i tried all options .. formated as ext2 and mount as ext2 . format as ext3 and mount as ext3 , format as ext4 and mount as ext4 .. 

i m sure that i am not making any such mistake .. or can u point me ? 

btw i have again partitioned it and made an ext4 partition and tried to mount it same error as just above post

---

### Post by oldfred on 2013-02-09
I do not understand why a newly formatted partition would have issues, but you can try fsck? Not sure if it will help or not? Run on all 4 partitions and check which device they are mounted as.

sudo fdisk -lu

Then use sdX1 thru sdX4 where X is the drive sdb, sdc etc.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

