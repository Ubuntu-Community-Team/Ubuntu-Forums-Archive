---
title: "transfer full hard drive from NAS to ubuntu server"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by rich30 on 2015-06-17
Hi guys, just got an HP Microserver as a replacement for my current NAS. I intend to install ubuntu server but before I do so can I ask a probably stupid question. The drives in the NAS are formatted using NFS and have a lot of data on them. Once I've installed ubuntu server can I just mount the drives in the server or will I need to reformat them?

---

### Post by Duck_Dude on 2015-06-17
Ubuntu will be able to read them natively.  I can't remember if they will automatically mount or not, and you will get better performance if you eventually end up formatting them (to ext3/4) but to just get started you'll be good to go.

---

### Post by steeldriver on 2015-06-17
What type / brand of NAS is it? I don't think the drives themselves are likely to be "formatted using NFS" - afaik NFS is a distributed file system *protocol* rather than an actual FS type

If the NAS uses RAID you may have to do more work to get it recognized and mounted. Some NASes use an ext2/3/4 FS but with a large block size that causes additional headaches.

You'll know more once you try to attach them

---

### Post by mastablasta on 2015-06-18
though if they are actually NTFS, they should be able to mount. unless it was some strange RAID setup.

---

### Post by cariboo on 2015-06-18
Before moving disks around, if you have remote access via terminal:

```
fdisk -l
```

will show a list of drives and partitions, and how they are formatted.

Most of the NAS software I looked at several years ago was [BSD]("https://en.wikipedia.org/wiki/Berkeley_Software_Distribution") based, so you may have to run the above command as root.

---

