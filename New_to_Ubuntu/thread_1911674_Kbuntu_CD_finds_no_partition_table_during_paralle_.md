---
title: "Kbuntu CD finds no partition table during paralle installation with Windows 7"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by HobbsTunaSandwich on 2012-01-19
As it is says on the tin. I downloaded the 11.10 kubuntu CD and wanted  to install it in combination with windows 7. Starting the installation,  the menu option of a parallel installation is missing and in manual mode  it shows just one big, free disk.

Booting ubuntu from CD, the partition manager tells me:

"No valid partition table was found on this device."

fdisk -lu    returns absolutely nothing. 

In the windows partition manager I find:
```

Lenovo_Recovery (Q:)   |   15.63GB   |  NFTS  |  Primary Partition
Windows7_OS (C:)       | 448.96GB    |  NFTS  |  Boot, Page File, Crash Dump, Primary Partition
System_DRV             |     1.17GB  |  NFTS  |  System, Active, Primary Partition
```Using a GParted I find again no partition table but the following partitions:
```

/dev/sde1    ntfs     System_DRV             1.17GB   boot 
/dev/sde2    ntfs     Windows7_OS       448.96GB
/dev/sde3    ntfs     Lenovo_Recovery   15.63GB
```The obvious conclusion is that something, presumably the strange  recovery partition, has Ubuntu confused. What can I do about this without  grilling my existing operating system?

---

### Post by mastablasta on 2012-01-19
or you could be having too many primary partitions. though it says there are only 3. 
 
another thing.... create emtpy disk space (a non formated partition) using windows disk manager and retry with install. if it find the empty disk partition you would be able to install on it.

---

