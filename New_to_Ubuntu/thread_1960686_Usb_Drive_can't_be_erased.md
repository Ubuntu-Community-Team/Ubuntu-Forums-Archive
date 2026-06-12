---
title: "Usb Drive can't be erased?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-04-17
I was putting 12.04 on a usb drive and it failed about half way through and now it says the usb drive is always busy so I can't do anything with it. I opened up Disk utility and when I try and re-format it, it says "One or more partitions are busy on /dev/sdb"

If I un-mount it and try to delete the part ion it say "Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=16384"

Any Help would be appreciated.

---

### Post by oldfred on 2012-04-17
Try to unmount or use liveCD so it is not mounted. If not sdb1 change to that partition.

#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Andrew_P on 2012-12-05
In Disk Utility, first click on the "Unmount _V_olume" button, then click on the "Format _D_rive" button.  It should then allow you to format the USB drive.

---

### Post by C.S.Cameron on 2012-12-05
Most flash drives are good for about 10000 writes, many are good for much less.
When a flash drive fails for this reason, (and others), it is still readable but not writable.
Most good flash drives have a good warranty, 5 years to life, if yours doesn't let us know the brand name.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

