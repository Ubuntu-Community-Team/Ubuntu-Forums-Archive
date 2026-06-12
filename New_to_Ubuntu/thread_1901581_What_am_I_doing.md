---
title: "What am I doing?"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by jiryan2316 on 2011-12-28
So I really want to download Ubuntu 11.10 and just replace my current OS, but it seems that I can not get it to copy to a disk.  How do I scrap Windows and use Ubuntu?

---

### Post by PaulHA2 on 2011-12-28
Here are directions for setting up the installer on a key/disc: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by Bucky Ball on 2011-12-28
Use the install CD.

When you get to the partitioning part of the install choose 'Something Else' which really means manual partitioning. Delete all your partitions then create partitions for Ubuntu and apply them. The installation should then proceed as per normal. This is the basics for your partitions:

/ = where the operating system goes - 15-20Gb fine;
/home = where your personal data goes - big as you like cos you are putting all your data there;
/swap = swap - 2Gb plenty.

All these are defaults in the partitions section, although you can create whatever you like, for instance;

/furniture
/finance 

The other option is to boot the install CD then 'Try Ubuntu'. Use Gparted (partition editor) and delete all your NTFS partitions (which is where Windows live) until you have an empty drive. Reboot and let the Ubuntu install do the rest, BUT you might not want the way that it partitions and organises the drive. 

Welcome to the forums and good luck. ;)

---

### Post by collisionystm on 2011-12-28
> **jiryan2316 said:**
> So I really want to download Ubuntu 11.10 and just replace my current OS, but it seems that I can not get it to copy to a disk.  How do I scrap Windows and use Ubuntu?

If you want to replace windows completely, do not use wubi.

go here

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

go to step 2, and click, SHOW ME HOW

---

### Post by mike555 on 2011-12-28
You need to write it to a disk as an image , you might need an iso writer ,like this ;
[http://www.freeisoburner.com/](http://www.freeisoburner.com/)

---

### Post by mastablasta on 2011-12-29
> **Bucky Ball said:**
> Use the install CD.

When you get to the partitioning part of the install choose 'Something Else' which really means manual partitioning. Delete all your partitions then create partitions for Ubuntu and apply them. The installation should then proceed as per normal. This is the basics for your partitions:

/ = where the operating system goes - 15-20Gb fine;
/home = where your personal data goes - big as you like cos you are putting all your data there;
/swap = swap - 2Gb plenty.

All these are defaults in the partitions section, although you can create whatever you like, for instance;

/furniture
/finance 

The other option is to boot the install CD then 'Try Ubuntu'. Use Gparted (partition editor) and delete all your NTFS partitions (which is where Windows live) until you have an empty drive. Reboot and let the Ubuntu install do the rest, BUT you might not want the way that it partitions and organises the drive. 

Welcome to the forums and good luck. ;)

or he can skip this and just select replace Windows with Ubuntu.

either way downloading and buring the ISO image to a CD or putting it to USB is the first step.

---

