---
title: "rsync - why need sudo to run for USB - HD?"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by fisheater on 2012-09-15
Hi,

Problem: rsync permissions on NAS to desktop USB HD.

Background: 
I use NAS4Free via NFS. I am using rsync to backup my data to the USB HD.
```
rsync -r -t -v --progress --delete /mnt/NAS/Data /media/USB_Offsite
```
This command does not work, but if I run it as sudo it works:
```
sudo rsync -r -t -v --progress --delete /mnt/NAS/Data /media/USB_Offsite
```

I am puzzled why I need to run this as sudo if my /mnt and /media are on my local machine and mounted with my permissions. My thoughts are that my /media/USB_Offsite are not mounted with full permissions. It is auto-mounted when the USB-HD is turned on.

Suggestions?

Thanks 

FE

Bonus question: 
how can I exclude a folder via rsync? I have tried a few different syntax variations, but it always seems to fail (i.e. It copies the excluded folder).

```
rsync -r -t -v --progress --delete –exclude='/mnt/NAS/Videos' /mnt/NAS/Data /media/USB_Offsite
```
I tried –exclude='Videos' but all folders and subfolders with Video in it were skipped.


TY

---

### Post by Dennis N on 2012-09-15
Your --exclude option: Try

```
--exclude=/mnt/NAS/Videos/
```

And be sure there is a double dash before exclude.

---

### Post by Hadaka on 2012-09-15
Hi, exclude folder example..

[http://www.garron.me/linux/exclude-folder-rsync-backup.html](http://www.garron.me/linux/exclude-folder-rsync-backup.html)

---

