---
title: "No space for updates ona new install?"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by Garnett on 2014-11-25
Hi there. I've recently installed Ubuntu on a new laptop, and everything seemed okay. But then it tried to update a week or so later and an error message popped up saying there was no space on "boot" for the necessary updates and that updating of packages had failed.

I cannot remember the exact wording of the errors, and I cannot recreate the problem at will-but it occurs every time the computer tells me it needs to update.

I'm not sure how to determine the problem (or why there is a problem, given this is new installation) let alone how to fix it.

Any help gratefully received.

---

### Post by yancek on 2014-11-25
This is a pretty common problem when people create a separate boot partition. Often it is too small and doing an update and adding kernels creates the problem.   Did you do that during the install?  Open a terminal and run this command:```
sudo fdisk -l
```
and post the output here.  While you are in the terminal also run:```
df -h
```
The first command shows drives/partitions, the second shows size and space used.

---

### Post by slickymaster on 2014-11-25
@yancek:
I've edit your post, adding code tags to it. Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when writing code in posts.

---

### Post by Garnett on 2014-11-25
Thanks for helping, Yancek.

In terms of the installation, as far as I am aware, I did everything as recommended by the installation process - nothing unusual.

The output of fdisk -l:[I]
```
[/I]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT

Disk /dev/mapper/sda3_crypt: 249.3 GB, 249263292416 bytes
255 heads, 63 sectors/track, 30304 cylinders, total 486842368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 245.1 GB, 245085765632 bytes
255 heads, 63 sectors/track, 29796 cylinders, total 478683136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4173 MB, 4173332480 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8151040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

Output of df -h:[I]
```
[/I]Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  225G  6.0G  208G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        384M  1.1M  383M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  152K  1.9G   1% /run/shm
none                         100M   40K  100M   1% /run/user
/dev/sda2                    237M  212M   13M  95% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
```

---

### Post by slickymaster on 2014-11-25
@Garnett:
Please see my [post #3]("http://ubuntuforums.org/showthread.php?t=2254182&p=13174395&viewfull=1#post13174395") regarding the use of code tags. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Garnett on 2014-11-25
Trying to find out more myself, and I've found [this thread]("http://ubuntuforums.org/showthread.php?t=2240240"), which points to [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093") which seems to fit my details, in that I opted for an encrypted install.Still not sure how to fix it though.

---

### Post by Bashing-om on 2014-11-25
@Garnett; Hello;

Please observe the up posts.

As to the situation at hand:
You are also a victim of a bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093) <- *Bug: /boot created to small:
Please add your voice to the report.

For the resolution in your case to alleviate this condition, run terminal commands:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` as apt-get now has the ability to remove old kernels; and try and install the latest kernel.
Let is know how it goes.

[INDENT][INDENT]best regards
[/INDENT][/INDENT]

---

### Post by Garnett on 2014-11-25
Bashing-Om, thanks a lot. That seems to have fixed it.

---

### Post by Bashing-om on 2014-11-25
Garnett; Great !

Pleased all has worked out.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

