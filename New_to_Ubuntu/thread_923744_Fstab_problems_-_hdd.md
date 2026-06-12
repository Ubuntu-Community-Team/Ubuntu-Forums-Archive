---
title: "Fstab problems - hdd"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by boeding on 2008-09-18
Hello,
I'm trying to get my data hard drives to auto mount at boot. But I get an error saying that there is an error in my fstab file and that the destination cannot be found. Here is what i have in my fstab.

/dev/sdb5 /media/Movies auto ext3 defaults 0 0
/dev/sda5 /media/Movies_2 auto ext3 defaults 0 0
/dev/sdc5 /media/Media auto ext3 defaults 0 0

I do have the folders located at /media/<folder name>, and the hard drives are ext3. any help would be nice.

---

### Post by sisco311 on 2008-09-18
try:
> 
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/Movies ext3 relatime 0 2
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/Movies_2 ext3 relatime 0 2
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/Media ext3 relatime 0 2
where xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is the uuid of the partition.
to get the uuid of a partition:
```
sudo vol_id -u /dev/sd***XY***
```

---

### Post by boeding on 2008-09-18
Thank you, 
I just deleted the "auto" from the fstab lines and it worked great.

---

### Post by sisco311 on 2008-09-18
Cool!

If you have multiple hard disks it's recommended to mount the partitions by UUID.
/dev/sd**XY** can change after a reboot while the uuid is a unique identifier of a partition.

---

