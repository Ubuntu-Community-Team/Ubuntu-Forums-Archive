---
title: "partitions problem"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by magicuzor on 2013-03-01
Hello. I installed last night ubuntu 10.12 and I selected the options that installs ubuntu over the windows 7 (thinking that I will install win7 later).

Now I can't see my windows partitions at all. I don't have permissions to mount my hdd drive and df -h says: 

> /dev/sda1       455G  3.6G  429G   1% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           764M  916K  763M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  252K  1.9G   1% /run/shm
none            100M   32K  100M   1% /run/user

The cachy thing is that last night I saw my partitions dev/sda1,dev/sda2,dev/sda3 exactly how they are in windows.
I really need them back, I didn't save a thing from my important things.

How can I see them? At least to copy them to an external drive or something

---

### Post by Impavidus on 2013-03-01
When you installed, did you select "use entire disk" or "something else" and then select you windows partition to install ubuntu on? In the first case everything is gone, meaning that you need recovery tools to get information back. Don't use the disk in that case, and only boot from your live disk. In the other case your windows system is gone, but your data partition should still be present. You indicated you still saw the partitions (specifically sda2 and sda3, which have not been mounted by ubuntu), so let's assume the latter.

Can you try the commands (note the lower case L)```
sudo fdisk -l
sudo blkid
```It should list all partitions present on your system, so that we can see whether the windows partitions are still present. If they are present, it should be possible to mount them.

Besides, I assume that you meant 12.10. Also, if you want to dual boot, it's easier but not mandatory to install windows first and ubuntu later.

---

