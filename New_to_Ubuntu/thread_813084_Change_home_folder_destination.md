---
title: "Change home folder destination"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by das letzte einhorn on 2008-05-30
I had to reinstall Ubuntu a few times to make it work, and during the first install I moved all my documents to my second hard drive, which I setted up as ext2 /home. However, I could not fix the mount point during the following Ubuntu setups because it would have formatted again, and therefore would have destroyed my documents. I have found this tutorial: [http://ubuntuforums.org/showthread.php?t=250104](http://ubuntuforums.org/showthread.php?t=250104) , which is when the other partition is empty, but for my case, I just want to change the destination; none of my documents needs to be moved. Technically, to find my documents the location is /media/sdb2/xavier ; this is where the first install I did would lead me if I click on Documents in the menus. Is there a quick way to fix this, like in Windows?

Thanks!

---

### Post by Duck2006 on 2008-05-30
When you reinstall ubuntu don't tell it to format the home folde just the / root folder. This may help.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sisco311 on 2008-05-30
Edit your fstab(assuming /dev/sdb2 is the partition):
```
gksu gedit /etc/fstab
```and add this line:
> /dev/sdb2/ /home auto defaults 0 2If you want to mount the partition by UUID:
```
sudo blkid /dev/sdb2
```> UUID=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx /home auto defaults 0 2delete the files from the old home:
```
sudo rm -fr /home/*
```mount the new one:
```
sudo mount -a
```

---

### Post by drs305 on 2008-05-30
> **sisco311 said:**
> 
```
sudo rm -fr /home/*
```
mount the new one:
```
sudo mount -a
```

I would suggest in case something goes wrong:
From:
```
Change this: sudo rm -fr /home/*
```
To:
```

sudo mkdir /home.old
sudo mv /home /home.old
```

---

