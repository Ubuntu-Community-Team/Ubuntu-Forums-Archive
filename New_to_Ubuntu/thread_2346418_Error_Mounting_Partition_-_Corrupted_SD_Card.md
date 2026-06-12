---
title: "Error Mounting Partition - Corrupted SD Card?"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by alastaircodd on 2016-12-14
Been trying to mount a partition on an SD card in a virtual machine. The SD card contains a raspberry pi image, consisting of two partitions; boot, and filesystem. I'm able to mount boot without any problems, but I consistently get the error message "Error mounting filesystem." This problem persists even after formatting and re-imaging the drive, and I've encountered no problems with other SD cards. Is the SD card corrupted? The error message is as follows: 

> Error mounting /dev/sda2 at /media/xxxxx/yyyyyyy: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/xxxxx/yyyyyyy"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
 (udisks-error-quark, 0)

Please could you advise me what I need to do in order to mount this partition.

---

### Post by Geoffrey_Arndt on 2016-12-14
Does the boot partition contain a different filesystem such as Fat32?   The error on the other partition may be a permissions issue.    If so, you would need to do this:

If username = bob and partition named data,

[U]sudo chown bob:bob /data

then
[/U]
_    sudo chmod ug+rwx,o+rx /data_

---

