---
title: "Can't find external journal. error"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by hopelessone on 2015-06-12
Hi,

```
blade@unicorn:~$ sudo fsck /dev/sdh1
fsck from util-linux 2.25.1
e2fsck 1.42.10 (18-May-2014)
Can't find external journal

/dev/sdh1: ********** WARNING: Filesystem still has errors **********


```

I read that:

> Write a new journal to the partition
# tune2fs -j /dev/<partition>
Run an fsck to repair the partition
# fsck -p /dev/<partition>

or

> tune2fs -f -O ^has_journal /dev/XXX
   e2fsck -fp /dev/XXX
   tune2fs -J device=/dev/YYY /dev/XXX

This will remove the journal from the filesystem, run e2fsck
to fix whatever problems it finds, then re-add the journal
device (if you have one, otherwise just use "tune2fs -j" to
add an internal journal).

or

> Now how do I fsck the filesystem?

Here's a workaround for now:

debugfs -w /dev/group-a/ums
debugfs: ssv journal_uuid null
debugfs: ssv journal_inum 0
debugfs: feature ^needs_recovery
debugfs: feature ^has_journal
debugfs: quit

... and then run e2fsck -f on the file system.

What's the recommended process to fix? So if I write a new journal to the partition will it destroy the existing files?

Thanks,

---

### Post by hopelessone on 2015-06-12
tried:

```
blade@unicorn:~$ sudo tune2fs -f -O ^has_journal /dev/sdh1
tune2fs 1.42.10 (18-May-2014)
The needs_recovery flag is set.  Please run e2fsck before clearing
the has_journal flag.
blade@unicorn:~$ sudo e2fsck -fp /dev/sdh1
/dev/sdh1: Can't find external journal

/dev/sdh1: ********** WARNING: Filesystem still has errors **********

blade@unicorn:~$ 

```

and

```
blade@unicorn:~$ sudo tune2fs -j /dev/sdh1
tune2fs 1.42.10 (18-May-2014)
The filesystem already has a journal.
blade@unicorn:~$ sudo tune2fs -J /dev/sdh1
tune2fs 1.42.10 (18-May-2014)

Bad journal options specified.

Journal options are separated by commas, and may take an argument which
	is set off by an equals ('=') sign.

Valid journal options are:
	size=<journal size in megabytes>
	device=<journal device>
	location=<journal location>

The journal size must be between 1024 and 10240000 filesystem blocks.

```

Any ideas?

---

### Post by hopelessone on 2015-06-14
anyone know what to do?

---

### Post by hopelessone on 2015-06-17
please help, I have alot of data

---

### Post by hopelessone on 2015-06-17
```
blade@unicorn:~$ sudo dumpe2fs /dev/sdh1 | more
dumpe2fs 1.42.10 (18-May-2014)
Filesystem volume name:   <none>
Last mounted on:          /mnt/hdd_7
Filesystem UUID:          8603d83c-a401-4509-a829-8e14c0cbf9ad
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype needs_recover
y extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isi
ze
Default mount options:    journal_data debug user_xattr acl MNTOPT_16 MNTOPT_18 
MNTOPT_19 MNTOPT_20 MNTOPT_21 MNTOPT_24
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61054976
Block count:              244190000
Reserved block count:     0
Free blocks:              5710362
Free inodes:              60619391
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Last mount time:          Sat Jun  6 15:38:16 2015
Last write time:          Mon Jun 15 10:53:44 2015
Mount count:              172
Maximum mount count:      24
Last checked:             Fri Nov 14 08:17:13 2014
Check interval:           15552000 (6 months)
Next check after:         Wed May 13 07:17:13 2015
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Journal UUID:             00000000-0000-0000-0400-00001454af8c
Default directory hash:   HASHALG_240
Directory Hash Seed:      00000000-0000-0000-0000-000014000000
Journal backup:           type 113

```

any help?

---

### Post by hopelessone on 2015-06-18
There is no information on google about this error, interesting no-one knows?

---

### Post by hopelessone on 2015-06-20
Anyone?

1TB Hard Drive

```
blade@unicorn:/media/blade/056d7c77-55d6-4ae8-9e5c-419983490086/backup$ dmesg | tail
>>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[77975.897906] hfs: can't find a HFS filesystem on dev sdc2
[77982.990374]  loop3: unknown partition table
[77983.147104] EXT4-fs (loop3): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[77985.717297] EXT4-fs (loop0): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[77988.840510] EXT4-fs (loop1): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[77991.576749] EXT4-fs (loop2): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[77993.965538] EXT4-fs (loop3): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[78146.311118] EXT4-fs (loop0): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)
[78910.183737] EXT4-fs (loop4): bad geometry: block count 125778361453360 exceeds size of device (244190000 blocks)

```

---

### Post by hopelessone on 2015-06-24
are the hard drive contents stuffed? help....(sinking sound)

---

