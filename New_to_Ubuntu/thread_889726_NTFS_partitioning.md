---
title: "NTFS partitioning"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-08-14
I've just installed 500gb SATA hard disk as slave. I wan't to use it as a NTFS drive, But I don't if ntfs-3g can effectively use partitions of such huge sizes. I've earlier used an external 160gb IDE disk as a single ntfs drive and it used to take a lot of access time. Plz help

thanq

---

### Post by LowSky on 2008-08-14
First thing is Gparted cannot create NTFS partitions. You will have to create it from Windows
second NTFS can see/use such large partitions as I am doing so right now.
third SATA is faste rthan IDE
Forth NTFS is horrible about Journaling which can increase access time on less used information

---

### Post by reponzo01 on 2008-08-14
> **LowSky said:**
> First thing is Gparted cannot create NTFS partitions. You will have to create it from Windows


Actually, GParted can indeed create NTFS partitions. I just did it a couple of days ago. [http://gparted.sourceforge.net/screens/gparted_7_big.jpg](http://gparted.sourceforge.net/screens/gparted_7_big.jpg) -> that's directly from GParted's site.

---

### Post by Paqman on 2008-08-14
> **karthikophobia said:**
> I've earlier used an external 160gb IDE disk as a single ntfs drive and it used to take a lot of access time. 

That's mostly because it was an external drive. You're limited by the speed of the port you're plugging it into, which could be quite slow in the case of an older USB port. You'll find an internal drive will be a LOT faster.

You can use the package [ntfs-config](apt:ntfs-config) if you want to start using your new drive without messing around with fstab entries.

---

### Post by LowSky on 2008-08-14
> **reponzo01 said:**
> Actually, GParted can indeed create NTFS partitions. I just did it a couple of days ago. [http://gparted.sourceforge.net/screens/gparted_7_big.jpg](http://gparted.sourceforge.net/screens/gparted_7_big.jpg) -> that's directly from GParted's site.

I was going on the fact that when I opened Gparted last week NTFS was greyed out. Is there a difference with the one Ubuntu installs over the Sourceforge version?

---

### Post by karthikophobia on 2008-08-14
The IDE drive I mentioned above worked on xp much quicker than in ubuntu. So I thought that the problem was with partitioning. I also remember reading somewhere that large ntfs partitions take longer access time.

thanx again

---

### Post by Gannon8 on 2008-08-14
> **LowSky said:**
> I was going on the fact that when I opened Gparted last week NTFS was greyed out. Is there a difference with the one Ubuntu installs over the Sourceforge version?

You have to install ntfsprogs in order to do much to NTFS partitions.
```
sudo apt-get install ntfsprogs
```

---

### Post by LowSky on 2008-08-14
> **karthikophobia said:**
> I also remember reading somewhere that large ntfs partitions take longer access time.


Initial Read time, yes, but transfer speeds should be the same.

Thing to take into account are USB cables, connecting to 1.1 USB ports trying to access infor while tranfersing data over USB is a bad idea too

---

### Post by Gannon8 on 2008-08-14
> **LowSky said:**
> Initial Read time, yes, but transfer speeds should be the same.

Thing to take into account are USB cables, connecting to 1.1 USB ports trying to access infor while tranfersing data over USB is a bad idea too

I know. My laptop only has USB 1.1 and it is slow. I wish it could boot from a USB disk.

---

### Post by karthikophobia on 2008-08-14
> **LowSky said:**
> Initial Read time, yes, but transfer speeds should be the same.

Thing to take into account are USB cables, connecting to 1.1 USB ports trying to access infor while tranfersing data over USB is a bad idea too
I have USB 2.0 and the problem was with accessing thee information, not transfering.

---

