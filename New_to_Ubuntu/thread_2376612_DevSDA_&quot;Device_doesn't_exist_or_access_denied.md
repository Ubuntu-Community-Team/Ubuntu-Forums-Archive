---
title: "/Dev/SDA &quot;Device doesn't exist or access denied&quot;"
date: 2017-11-04
forum: New to Ubuntu
---

### Post by thegummybear on 2017-11-04
Hey Guys; i'll start this off with a wonderful video link:

[https://www.youtube.com/watch?v=7liZPe-KqG8](https://www.youtube.com/watch?v=7liZPe-KqG8)

This has been plaguing me for a week. We received a new 360 camera with a separate box for stitching however it was DOA (faulty hardware); we need it for a shoot on Tuesday and with no time to get a replacement I cloned the m.2 drive inside to a spare SSD and have been trying to get it to boot on another machine; however the above video is what comes up! Any and all help would be hugely appreciated!

Regards,

---

### Post by leunam12 on 2017-11-06
I think that if you clone your disk you have to have to boot from the USB live session and then manually modify the fstab file with the new UUID numbers for the new partitions. If you have not done that, I would start there. boot from usb and post the results of ```
lsblk
``` ```
sudo fdisk -l
``` and ```
blkid
```

---

### Post by leunam12 on 2017-11-06
also mount the root partition on the ssd and then do ```
cat /media/ubuntu/<partition_name>/etc/fstab
``` and post the results. <partition_name> is the actual name of the partition mount point

---

