---
title: "Not able to copy files to other drives/partitions except home"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by LastDino on 2014-04-29
I can't copy files from home directory to my storage partition for some reason. This was not a problem with Ubuntu but Xubuntu seems to require me to open my file manager as root to do the same.  I would like to avoid that if possible. Further info:  I'm using Xubuntu 14.04 LTS. Storage partition is basically extra partition I like to make in ext4 on a same HD as I've installed OS just to store downloaded files etc.  If it helps, VM also refused to store VDI file on storage partition too.  My best guess is that it has something to do with permissions as those partitions are getting mounted just fine and I can do everything as root, but I'm not sure. But I haven't really changed any default settings of that.  Any solutions?

---

### Post by JeQhdMD on 2014-04-29
Thanks to DennisN, here is what worked for me in a similar situation (except I had formatted a PNY 32 GiB flash card to ext4 instead).

[http://ubuntuforums.org/showthread.p...9#post12957049]("http://ubuntuforums.org/showthread.php?t=2211159&p=12957049#post12957049")"

If the device's file system remains as msdos fat32, the permissions issue doesn't seem to arise.

---

### Post by LastDino on 2014-04-29
That worked like a charm! Thank you for quick reply. Now I remember, I used NTFS for storage when I was using Ubuntu. No wonder.

---

