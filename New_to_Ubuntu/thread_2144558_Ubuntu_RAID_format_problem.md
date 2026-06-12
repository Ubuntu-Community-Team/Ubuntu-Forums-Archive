---
title: "Ubuntu RAID format problem"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by yendorii on 2013-05-12
I'm totally new to ubuntu and I'm trying to get up to speed as quickly as possible. I've just set up a server with a boot drive and a 5 drive raid array. I'm trying to use gparted to format the raid array in ext4. I set it up as a gpt partition table and I keep getting an error that I'm unsure how to fix. The error I get is as follows:

[COLOR=#000][FONT=times new roman]GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Create Primary Partition #1 (ext4, 8.19 TiB) on /dev/sdb  00:00:36    ( ERROR ) **[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] create empty partition  00:00:22    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sdb1
start: 2,048
end: 17,578,055,679
size: 17,578,053,632 (8.19 TiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] set partition type on /dev/sdb1  00:00:14    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *new partition type: ext4*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] create new ext4 file system  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***mkfs.ext4 -j -O extent -L "" /dev/sdb1***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]mke2fs 1.42.5 (29-Jul-2012)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================

I would very much appreciate any help that anyone can provide.

[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-13
I do not know RAID. Changed title to formatting with RAID.

Some threads discussing RAID issues, but now sure they will help.
[http://ubuntuforums.org/showthread.php?t=2084823](http://ubuntuforums.org/showthread.php?t=2084823)
[http://ubuntuforums.org/showthread.php?t=2140218](http://ubuntuforums.org/showthread.php?t=2140218)
[http://manpages.ubuntu.com/manpages/hardy/man5/mdadm.conf.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/mdadm.conf.5.html)

---

