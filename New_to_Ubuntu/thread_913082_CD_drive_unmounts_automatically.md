---
title: "CD drive unmounts automatically"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Raazka on 2008-09-07
Hi,

I have an old desktop running Hardy, and it's having trouble reading CDs.

When I put any CD in the drive, the drive mounts normally, but within a second or two it automatically unmounts. I get a glimpse of the CD's contents, but not enough time to do anything. The drive is just a generic CD/DVD drive, nothing special.

I was able to install Hardy with a CD originally, so I don't know what happened to the drive to make it suddenly stop working. 

Thanks.

---

### Post by Raazka on 2008-09-07
I should probably note that the desktop in question is not only ten years old, but a random mixture of parts. I think the CD drive is original, but I'm not certain.

---

### Post by Sycron on 2008-09-07
try to mount the cdrom manually.

```
sudo mount /dev/src0 /mnt && nautilus /mnt
```

---

### Post by Raazka on 2008-09-08
When I try to mount it manually, it says "/dev/src0/ does not exist."

---

### Post by Sycron on 2008-09-09
> **Raazka said:**
> When I try to mount it manually, it says "/dev/src0/ does not exist."

Sorry it's ```
sudo mount /dev/scd0 /mnt && cd /mnt && nautilus /mnt
```

---

### Post by Raazka on 2008-09-19
When I mount it using that code, an error popped up which said "mount: no medium found."

---

### Post by Sycron on 2008-09-21
I think it means that is no CD in that drive...

---

### Post by Raazka on 2008-09-21
It says this for all sorts of disks, unfortunately. Not only program CDs, but also music CDs. I originally installed Ubuntu on this computer using a CD, and this really confuses me.

---

### Post by Sycron on 2008-09-21
Try booting the livecd again. If will not work the CD drive is unfunctional .

---

### Post by skottesd on 2010-11-06
You're not alone in this. I'm trying Ubuntu on an old (pre-2000) destop I had in my garage which has mixed parts as well and it's doing exactly the same thing.

---

