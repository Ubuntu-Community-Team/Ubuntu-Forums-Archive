---
title: "HOWTO: Acessing memory card reader on HP all-in-one through network"
date: 2009-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ionospheric on 2009-04-29
Here's how to access the memory card on an HP all-in-one:

(for example, to copy pictures from a digital camera to the computer)

I used the information from this page
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00149194]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00149194")

Steps:

1. Find out the IP address of the printer

2. Create a mount point

```
sudo mkdir /mnt/HP6100
```


3. Mount the device
```
mount -t smbfs //192.168.0.6/Memory_Card  /mnt/HP6100
```


Note: make sure you have SMBFS installed before you try to mount

```
sudo apt-get install smbfs
```

---

### Post by magnetra7 on 2010-05-13
> **ionospheric said:**
> Here's how to access the memory card on an HP all-in-one:

(for example, to copy pictures from a digital camera to the computer)

I used the information from this page
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00149194]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00149194")

Steps:

1. Find out the IP address of the printer

2. Create a mount point

```
sudo mkdir /mnt/HP6100
```


3. Mount the device
```
mount -t smbfs //192.168.0.6/Memory_Card  /mnt/HP6100
```


Note: make sure you have SMBFS installed before you try to mount

```
sudo apt-get install smbfs
```

Thanks man, now I can use my Officejet as a NAS (well sort of). Great!

---

### Post by tnt533 on 2011-05-26
An easy alternative is simply to open Nautilus, click on connect to server in the <File> menu and choose <Windows Share> as the type of connection. Enter the IP address of the printer and then enter Memory_Card as the share name and off you go!

I use this method with my HP Officejet 7410.

---

