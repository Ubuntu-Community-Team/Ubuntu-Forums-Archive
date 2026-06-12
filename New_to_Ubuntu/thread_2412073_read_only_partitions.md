---
title: "read only partitions"
date: 2019-02-07
forum: New to Ubuntu
---

### Post by hesham.elsahhar on 2019-02-07
hello, i am new to Ubuntu after using windows for a long time, i have deleted windows and installed Ubuntu everything went well but i have discovered that my ntfs partitions is now read only i can't create or paste any files, most of solutions available didn't work for me as it occurs becuase of dual boot but currently i have Ubuntu only 
any suggestions ?

---

### Post by yancek on 2019-02-07
How many partitions?  Are you not able to write anywhere on the system?  If a system becomes read-only, it is often because there is a problem with the filesystem so you need to run the fsck command on each partition causing problems.   Examples and explanations at the link below and numerous other sites.

[https://www.thegeekstuff.com/2012/08/fsck-command-examples](https://www.thegeekstuff.com/2012/08/fsck-command-examples)

---

### Post by Dennis N on 2019-02-07
Not sure if this is your problem, but be aware that when you create a new ext4 partition with gparted, it is initially owned by root. To use it, you need to change ownership of the directory used as the mount point to your user.

If your user name is mary, and partition is mounted at /mnt/data

```
sudo chown -R mary:mary /mnt/data
```

Reboot, and you will have all necessary access.

---

### Post by hesham.elsahhar on 2019-02-09
sorry, i forgot to mention that the partitions are ntfs formatted

---

### Post by oldfred on 2019-02-09
If you have NTFS partitions, you then need to make sure in Windows that you turn off the fast start up. That leaves a hibernation flag set on all NTFS partitions and then the Linux NTFS driver will not mount them.

You also should not keep NTFS partitions unless you have Windows or Windows repair disk/flash drive. NTFS will need chkdsk or defrag periodically and you cannot do that from Linux. 
You may be able to mount read only (ro) and copy data to another drive.

       Force removal of hiberfil from Ubuntu
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

