---
title: "[SOLVED] Resize ubuntu partition while in ubuntu."
date: 2008-07-25
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-25
How can i resize Ubuntu's "main" partition while in Ubuntu.

---

### Post by avtolle on 2008-07-25
To resize a partition, the partition must be unmounted. Therefore, you need to use a Live CD to do this.

---

### Post by tamoneya on 2008-07-25
you cannot resize a partition while it is mounted so you cant do this while using ubuntu.  What you can do however is use the ubuntu liveCD.  This is the cd you used to install ubuntu initially.  It does not need to mount the root partition and therefore you can work on it with gparted or fdisk.  Here are the commands you should run from the liveCD to open a partition editor:```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by Paqman on 2008-07-25
Gparted is already installed on the LiveCD, just go to System > Admin > Partition Editor. No need to install anything.

---

### Post by cristo-father on 2008-07-25
> **tamoneya said:**
> you cannot resize a partition while it is mounted so you cant do this while using ubuntu.  What you can do however is use the ubuntu liveCD.  This is the cd you used to install ubuntu initially.  It does not need to mount the root partition and therefore you can work on it with gparted or fdisk.  Here are the commands you should run from the liveCD to open a partition editor:```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

Thank you.

---

### Post by jamesrfla on 2008-07-25
You can also go hear [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and download it and just wright it to a CD. Then you don't have to wait long for the Ubuntu Live CD to load or you can just use the Ubuntu Live CD.

---

