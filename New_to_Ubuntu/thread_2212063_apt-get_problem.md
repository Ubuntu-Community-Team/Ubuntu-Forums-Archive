---
title: "apt-get problem"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by windtsui on 2014-03-19
output from dmesg

-----------------------------------
upsd" capability=36  capname="block_suspend"
[ 1215.421686] type=1400 audit(1395221078.508:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=877 comm="cupsd" pid=877 comm="cupsd" capability=36  capname="block_suspend"
[ 4306.506456] EXT4-fs error (device sda1): __ext4_ext_check_block:492: inode #2360670: comm BrowserBlocking: bad header/extent: invalid magic - magic 71fe, entries 24589, max 7(0), depth 0(0)
[ 4306.506461] Aborting journal on device sda1-8.
[ 4306.506470] EXT4-fs error (device sda1) in ext4_orphan_add:2417: Journal has aborted
[ 4306.514861] EXT4-fs (sda1): Remounting filesystem read-only
[ 4306.514868] EXT4-fs error (device sda1) in ext4_ext_remove_space:2827: IO failure
[ 4306.515024] EXT4-fs error (device sda1): ext4_journal_start_sb:371: Detected aborted journal
[ 4306.515108] EXT4-fs error (device sda1) in ext4_reserve_inode_write:4476: Journal has aborted
[ 4306.544043] EXT4-fs error (device sda1) in ext4_reserve_inode_write:4476: Journal has aborted
[ 4306.578184] EXT4-fs error (device sda1) in ext4_ext_truncate:4380: Journal has aborted
[ 4306.590718] EXT4-fs error (device sda1) in ext4_reserve_inode_write:4476: Journal has aborted
[ 4306.596029] EXT4-fs error (device sda1) in ext4_orphan_del:2489: Journal has aborted
[ 4306.597965] EXT4-fs error (device sda1) in ext4_reserve_inode_write:4476: Journal has aborted
[ 4306.598222] journal commit I/O error
[ 4386.786810] init: Failed to write to log file /var/log/upstart/utorrent.log
--------------------------------------------------------------------

can anyone help

---

### Post by TheFu on 2014-03-19
Debian has recommended the use of **aptitude** over apt-get for years. It is almost always smarter. The dmeg output isn't all that helpful for apt-get issues. Please run these and post ****only the relevant output**** back here inside "code" tags - like below.

```
sudo aptitude update
sudo aptitude upgrade

```
Makes it easier to read - columns are aligned.

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
In the dmesg error you got, though, you can use "aa-complain /usr/sbin/cupsd" to allow cupsd to run with only a complaint.  Interesting that you would get an error at all like that; for some reason, apparmor is blocking it.  Maybe it's from an unusual path configured or something.

What output do you get when you 'sudo apt-get update' and 'sudo apt-get upgrade'?

-DM

---

