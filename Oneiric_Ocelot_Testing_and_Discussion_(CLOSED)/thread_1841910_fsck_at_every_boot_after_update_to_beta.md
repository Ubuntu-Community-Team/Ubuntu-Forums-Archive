---
title: "fsck at every boot after update to beta"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by hesee on 2011-09-10
Hi, I've upgraded to Oneiric beta from Natty. After that boot time increased, and I noticed that fsck is run every boot:
```
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda1: clean, 391342/610800 files, 1750408/2441216 blocks
/dev/sda5: clean, 75722/14589952 files, 1948189/58349312 blocks
```

Is that the reason for slow boot?

---

### Post by ajgreeny on 2011-09-10
Something must be very wrong with your filesystem for the check to run at every bootup.  Run the command ```
sudo tune2fs -l /dev/sdx#
``` where sdx# is your ubuntu root partition, and see what the output tells you, particularly the line near the top starting "Filesystem state:", which should end with "clean".  The output will also have two lines, **Mount count**, and **Maximum mount count**.  What numbers follow those entries?

It may also be worth booting to a live CD and running ```
sudo e2fsck /dev/sdx#
``` to see in more detail what the scan throws up by way of errors.

---

### Post by hesee on 2011-09-11
sudo tune2fs -l /dev/sda5
```
tune2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          /home
Filesystem UUID:          975d57ad-adb7-4131-8a0d-31a405ff0c2e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              14589952
Block count:              58349312
Reserved block count:     2917465
Free blocks:              56387997
Free inodes:              14513892
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1010
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Jul  1 02:18:46 2010
Last mount time:          Sat Sep 10 17:59:49 2011
Last write time:          Sat Sep 10 17:59:49 2011
Mount count:              22
Maximum mount count:      50
Last checked:             Fri May 13 18:26:59 2011
Check interval:           15552000 (6 months)
Next check after:         Wed Nov  9 17:26:59 2011
Lifetime writes:          17 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       11010972
Default directory hash:   half_md4
Directory Hash Seed:      5f46b80f-0b18-42d8-a173-3c2be08e3fa3
Journal backup:           inode blocks
```

Last checked is obviously not right?

---

### Post by sumski on 2011-09-11
hesee, i'm having the same issue (only using kubuntu) , also upgraded from Natty. It seems to me it's because filesystem doesn't get unmounted on reboot. I'm seeing fsck mesagges on every boot wich is quite annoying, and also worries me cause i'm getting deleted orhans all the time.

---

### Post by ajgreeny on 2011-09-11
> **hesee said:**
> sudo tune2fs -l /dev/sda5
```
tune2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          /home
Filesystem UUID:          975d57ad-adb7-4131-8a0d-31a405ff0c2e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              14589952
Block count:              58349312
Reserved block count:     2917465
Free blocks:              56387997
Free inodes:              14513892
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1010
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Jul  1 02:18:46 2010
Last mount time:          Sat Sep 10 17:59:49 2011
Last write time:          Sat Sep 10 17:59:49 2011
Mount count:              22
Maximum mount count:      50
Last checked:             Fri May 13 18:26:59 2011
Check interval:           15552000 (6 months)
Next check after:         Wed Nov  9 17:26:59 2011
Lifetime writes:          17 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       11010972
Default directory hash:   half_md4
Directory Hash Seed:      5f46b80f-0b18-42d8-a173-3c2be08e3fa3
Journal backup:           inode blocks
```Last checked is obviously not right?
That tune2fs output is not for your root partition but your separate /home partition.

What does your root partition say?

---

### Post by hesee on 2011-09-12
> **ajgreeny said:**
> That tune2fs output is not for your root partition but your separate /home partition.

What does your root partition say?

Yes, it's home. Here's root:
```
tune2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          0dd56355-5ce2-428d-a1fa-8b0fbb39d4fc
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              610800
Block count:              2441216
Reserved block count:     122060
Free blocks:              686802
Free inodes:              219449
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      595
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8144
Inode blocks per group:   509
Flex block group size:    16
Filesystem created:       Thu Jul  1 02:18:41 2010
Last mount time:          Mon Sep 12 09:18:53 2011
Last write time:          Sat Aug 20 21:06:57 2011
Mount count:              15
Maximum mount count:      28
Last checked:             Sat Aug 20 21:06:57 2011
Check interval:           15552000 (6 months)
Next check after:         Thu Feb 16 20:06:57 2012
Lifetime writes:          46 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       131834
Default directory hash:   half_md4
Directory Hash Seed:      b8547b76-f4da-4ec6-a966-64eadaebf751
Journal backup:           inode blocks

```

---

### Post by ajgreeny on 2011-09-14
No obvious problems showing in that, unfortunately, or not to me at any rate.

Sorry, but I think I am at the end of my knowledge, other than to suggest you boot to a live CD/USB, and with the root (or /home) partition unmounted, run the command ```
sudo e2fsck /dev/[COLOR=Red]sdax[/COLOR]
```[COLOR=Red]sdax[/COLOR] being your root partition, and report any error messages it throws back at you.  If that is OK do it again for /home and see if that is also OK.

---

### Post by hesee on 2011-09-22
Hi,
been away for a while. I did update today, noticed that boot window (that purple one with white/orange dots) displays something like "waiting for network interfaces". I had "auto eth0" in /etc/network/interfaces. Some configuration from past, i suppose, that is not relevant today. Don't know if there was anything wrong with fsck at all.

Anyway, that solved slow boot, actually, booting is now superfast :p

---

### Post by sumski on 2011-10-01
I solved my problem with (re)moving scripts in /etc/rc0.d/ and /etc/rc6.d/ - they got messed up by rcconf

---

