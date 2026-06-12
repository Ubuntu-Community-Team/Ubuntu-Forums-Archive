---
title: "Improving Rip Speeds"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by BrantlyMedders on 2008-09-01
Can anyone help me improve my rip speeds in Hardy?  Despite having a 20X DVD RW IDE drive, I can only rip at speeds around 3X.  None of my google results have turned up a useful result.  Most all of them revolve around using hdparm to turn DMA on, but this is the result I get when trying:

sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

I also get a similar result when doing sudo hdparm /dev/scd1 (which is just an IDE DVD drive:

/dev/scd1:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Is there anything I can do?  Currently I'm using GRIP to rip cd's, and have turned off CD paranoia.

---

