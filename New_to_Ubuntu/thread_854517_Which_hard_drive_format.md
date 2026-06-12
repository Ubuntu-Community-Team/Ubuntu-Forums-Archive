---
title: "Which hard drive format?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by tophue on 2008-07-09
I just bought a seagate external hard drive and want to be able to use it between windows xp and ubuntu 8.04, what format should I make the disk for best compatability?

---

### Post by Cypher on 2008-07-09
You can format it to NTFS and use ntfs-3g in Linux to access it, or you can format it to EXT3 and use explore2fs in Windows to access it.

However, stability wise I've found ntfs-3g to be way better in Linux than explore2fs on Windows. So the first option might your best bet..

---

### Post by tophue on 2008-07-09
Ok, so I want to format it to NFTS. How do I do this from a linux machine?

---

### Post by jamesrfla on 2008-07-09
You can also format it as FAT32 but NTFS is more. I had Ubuntu Desktop 7.04 and was able to read data on a NTFS drive. I am not sure I was able to wright but I was able to do that without installing anything on the Ubuntu and windows.

---

### Post by jamesrfla on 2008-07-09
You would want to use gparted to format the drive or use Windows utility.

---

### Post by LowSky on 2008-07-09
> **tophue said:**
> Ok, so I want to format it to NFTS. How do I do this from a linux machine?

You can't format to NTFS using Linux. YOu can do it from Windows.

FAT32 is the best option as long as files are no larger than 4GB, and can be read and create form both operating systems.

---

### Post by roquefilipe on 2008-07-09
> **LowSky said:**
> FAT32 is the best option as long as files are no larger than 4GB, and can be read and create form both operating systems.
Yes, I believe that FAT32 will be alright for you if the files aren't bigger than 4GB

---

