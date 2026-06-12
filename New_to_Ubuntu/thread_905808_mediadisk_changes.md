---
title: "/media/disk changes"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Sturatt on 2008-08-30
How can I make it so /media/disk is always the same? I have a 65 GB partition that I have told Deluge to download torrents to, but sometimes /media/disk/ isnt that same partition anymore. how can i make it so it is always the same?

---

### Post by drs305 on 2008-08-30
> **Sturatt said:**
> How can I make it so /media/disk is always the same? I have a 65 GB partition that I have told Deluge to download torrents to, but sometimes /media/disk/ isnt that same partition anymore. how can i make it so it is always the same?

/media/disk is actually a mount point. I will assume that you are talking about a device that you always want to mount to /media/disk. 

Is this is a removable drive? In any case, the solution is to list it in fstab (/etc/fstab) and identify it by UUID or label. If you identify it with either of the above it won't matter if it's internal or external as it will always be identified the same way. It would probably be best to make the mount point something other than 'disk' since that is a common name used by the system to mount removable drives.

If you need help putting an entry in fstab, post the results of:
```

sudo blkid
fdisk -l
cat /etc/fstab

```

and also include the name of the mount point, the partition you want mounted, and if you want to use a label, the name.

If you would prefer to do it yourself I've written a tutorial on how to use pysdm, a gui-based fstab editor. The link is in my signature block. Or here is a more official link:
[https://help.ubuntu.com/community/MoveMountpointHowto]("https://help.ubuntu.com/community/MoveMountpointHowto")

Welcome to the ubuntu forums.

---

