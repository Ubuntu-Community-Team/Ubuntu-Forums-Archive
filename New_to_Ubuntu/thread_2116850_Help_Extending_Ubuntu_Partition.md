---
title: "Help Extending Ubuntu Partition"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by kaneone on 2013-02-16
I want to extend my "ext4" partition with an unallocated partition. Here's how my partitions look:

[IMG]http://img72.imageshack.us/img72/2900/screenshotfrom201302162.png[/IMG]

What I thought I should do is:
1. Extend the "extended" file system by 75.00 GiB. After doing that, the unallocated file system will be above the linux-swap.
2. Now I think I should delete the linux-swap, but when I do that, it  moves "ext4" to "dev/sda5," which I'm not sure if that's a good idea.
3. Extend the "ext4" partition and leave 954.00 MiB.
4. Make a new linux-swap partition out of the 953.00 MiB unallocated partition.

This is my first time doing something like this, so I doubt I'm doing a  good job. Before I do all that, should I do something else instead?tion and leave 954.00 MiB.
4. Make a new linux-swap partition out of the 953.00 MiB unallocated partition.

This is my first time doing something like this, so I doubt I'm doing a  good job. Before I do all that, should I do something else instead?

---

### Post by DuckHook on 2013-02-17
You needn't apologize. There was a first time for all of us once.

1. BACKUP BACKUP BACKUP. Make sure you have Windows install/recovery disks. You are changing partitions. This is the single most dangerous operation for new users. Am assuming it's a MBR partitioning scheme, so you have maxed out your primary partitions.

2. If you are prepared to just create a new logical volume (rather than trying to extend some old ones), then it is much easier.

3. Depending on your data needs, another logical volume may actually be beneficial. You can place all of your pure data on it and it will be preserved through your next upgrade, even if you decide to wipe your existing OS and install from scratch (this would usually delete all existing data).

4. If agreeable to above option, then boot into LiveCD and start gparted. Do not do this from your existing install. Must boot into LiveCD. Increase geometry of sda4 to encompass all unallocated space.

5. New space will become part of sda4 but will have no file system. Therefore, highlight new space and choose "create new volume/partition", format file type to be ext4. If in doubt about anything, cancel all changes and start over or come back to forum for further instructions. Go so far as to quit gparted then relaunch to make sure all action buffers have been emptied. 

6. If entirely confident, click "Apply". You are now committed. This may very well take a long time. Once started it must not be stopped. Go for dinner, have a beer, walk the dog, but don't power down.

6. This will create a new volume that in your case the system will likely assign sda7. You now have a new logical volume. You will have to mount it in Ubuntu before you can use it. If you don't know how to mount, we will leave that to the next step.

You do not need to move swap or any of your existing volumes unless you want one big volume. Frankly, I don't see the advantage of that in your case. My install is always split into at least a separate / and /home, sometimes even more.

Good Luck, and back up all data on both Windows and Linux drives before proceeding, then check backup to make sure data is complete and readable.

---

