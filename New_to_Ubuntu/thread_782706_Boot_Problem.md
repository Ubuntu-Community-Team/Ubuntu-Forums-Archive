---
title: "Boot Problem"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-05
Hi,

When I boot up my computer, the terminal is displayed, and the following comes up:

> File system check failed. 
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

When I press CTRL+D, the computer then continues to boot up normally.
The log in /var/log/fsck/checkfs is:
> Log of fsck -C3 -R -A -a 
Mon May  5 11:12:52 2008

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/mmcblk0p1: 805 files, 41760/61980 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 76 files, 3545/44068 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  29:f8/08, 30:10/00, 31:09/00, 71:44/4e, 72:65/4f, 73:6c/20, 74:6c/4e
  , 75:4d/41, 76:44/4d, 77:33/45, 78:70/20, 79:6c/20, 80:61/20, 81:79/20
  Not automatically fixing this.
/dev/sda5: 5090 files, 197827/521984 clusters
/dev/sda7: clean, 24037/404000 files, 261525/807258 blocks
fsck.ext3: Unable to resolve 'UUID=bc4b12de-2d13-4283-8232-269aecbd0bfc'

fsck died with exit status 8

Mon May  5 11:12:58 2008
----------------

What is the problem here, and how can I solve it?

Thanks

---

### Post by frodon on 2008-05-05
Either your partition contains errors, and a "sudo fsck /dev/*linux_partition_name*" will fix them or your menu.lst and fstab file are pointing to a wrong partition (wrong UUID).

---

