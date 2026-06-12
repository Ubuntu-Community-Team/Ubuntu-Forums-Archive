---
title: "partitioning hard drive in 12.04"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by albaqui on 2013-11-21
My laptop is running perfectly. It has 250 GB hard drive. My present OS is Ubuntu 12.04 LTS. I want to partition so that I can install Windows 7 also. My almost whole space (241 GB) is occupied by Ubuntu. It shows 2 very small partitions also.
1. Can I partition this 241 GB which is in use safely? Can I Install windows 7 in that free space?
2. Can I get Windows free from website and install there without causing any problem to my original Ubuntu?

Thanks.

---

### Post by heir4c on 2013-11-21
For your partition table open a terminal and type:
```
parted -l
```

---

### Post by albaqui on 2013-11-21
Thanks. Can I partition using disc utility?  It is my main partition where Ubuntu is seated. Thanks

---

### Post by Bucky Ball on 2013-11-21
You need to boot from the LiveCD, get to a desktop and then launch Gparted. The partitions need to be UNMOUNTED! You can not resize a partition you are running the OS from.

---

### Post by ajeebkp23 on 2013-11-21
If you are not commandline addict you can use this little linux (as live cd) to do the same.

[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)

Now my comments based on my experience in partitioning, Don't change the starting of the partition just change the end point. If you change starting you might probably want to solve the issue regarding the Bootloader.

---

### Post by Impavidus on 2013-11-21
You can shrink your Ubuntu partition to make room for a Windows partition, craete that partition and then install Win7. Keep in mind that Windows wants a primary partition with boot flag and preferably at the start of the disk (before any extended partition). Installing Windows will cause one problem to your Ubuntu install, as it will overwrite the grub boot loader with it's own, ignoring the presence of Ubuntu, but this can be fixed easely by reinstalling grub via a live disk. For details we need the exact layout of your hard disk. For partitioning we recommend using a live disk and the tool gparted, which is installed by default on the live disk.

I think you can download a Windows install disk and install it for free provided you already have a valid product key. Else, you need to buy it.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

### Post by albaqui on 2013-11-21
thank you all.

---

