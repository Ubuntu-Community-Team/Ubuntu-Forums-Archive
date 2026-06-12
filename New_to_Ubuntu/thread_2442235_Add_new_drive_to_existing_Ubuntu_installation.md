---
title: "Add new drive to existing Ubuntu installation"
date: 2020-05-01
forum: New to Ubuntu
---

### Post by hemantpande87 on 2020-05-01
Hi, I have a windows 10 and Ubuntu 18.04.0 LTS on a single machine.

My windows installation has a C drive, D drive and E drive, each of round 500 GB. My Ubuntu installation size is approximately 120 GB.

I want to permanently move the E drive which is currently under windows installation, to existing Ubuntu installation. Please help me, how can I do that.

Thanks,
Hemant

---

### Post by jeremy31 on 2020-05-01
Moved to New to Ubuntu

---

### Post by dino99 on 2020-05-01
Simply use tool to format it under ubuntu  [https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu](https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu)
Then you can use it for data storage or system installation
If you install ubuntu on it, then  reinstall grub to grab that new system.
Later you also can add it to /etc/fstab to load it at boot time (for data, but not mandatory), after getting uuid via blkid

---

### Post by CelticWarrior on 2020-05-01
Knowing that you have a dual-boot - Windows is needed to correct eventual errors in NTFS partitions - you can keep it like it is now, assuming you want the non-system partition as a data storage only.

[The new Fast Startup feature existing in any Windows 8 or newer should be disabled]("https://www.windowscentral.com/how-disable-windows-10-fast-startup"). That done you can use the additional partitions in both OSes.

Now, if what you really want - it's not clear at all in your post - is to *change* the partitioning layout like, for example, remove one of your current NTFS partitions and "merge" the then unallocated space with the Ubuntu system partition, that is a lot more involved than the two different suggestions here, the re-formatting of said partition as EXT4 by dino99 and the usage "as is" by me, and is comes with additional risk of data loss. For that we also need  to know a lot more in order to provide instructions.

---

