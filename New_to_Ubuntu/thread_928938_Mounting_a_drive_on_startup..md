---
title: "Mounting a drive on startup."
date: 2008-09-24
forum: New to Ubuntu
---

### Post by russki_drewski on 2008-09-24
Hey, I'm running Ubuntu 8.04 with a dual boot between Windows Vista and I have my windows drive that I like to save all my files so that I can access them wether I'm in windows or Linux. However, when I start up the computer the drive is not mounted by default and I have to click on Places->60 GB Disc which then mounts the drive and opens a window to look at the drive contents.

So my question is this, how can I make it so that the drive will mount upon startup?


Thx,
Drewski

---

### Post by Vivaldi Gloria on 2008-09-24
> **russki_drewski said:**
> So my question is this, how can I make it so that the drive will mount upon startup?


You need to add your drive to /etc/fstab. There are guides around. Search them. See [[COLOR="Sienna"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?&t=283131") one for example.

---

### Post by Raffles10 on 2008-09-24
You need [ntfs-config]("http://flomertens.free.fr/ntfs-config/"). At boot it will automatically mount the drive in read/write mode.

```
sudo apt-get install ntfs-config
```

---

