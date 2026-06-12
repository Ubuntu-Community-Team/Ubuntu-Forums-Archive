---
title: "Installation of Ubuntu"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-24
i want to install ubuntu in separate drive.. i hav windows 8 consumer preview in another drive(C:).. when i tried to install ubuntu using wubi in D: drive some error message is coming.. i tried to install with boot options but there also its showing option for erasing all the contents and installing ubuntu...

i want to install Ubuntu in D: drive and i like to have Windows 8 in C: wat i have to do...

---

### Post by Bucky Ball on 2012-03-24
Not use Wubi. That is intended for installing inside Windows, not dual-booting on separate partitions. You need to download the desktop ISO, burn a CD from it and boot from the CD. When you get to the options, choose 'Try Ubuntu' (without installing) and see how you go. Let us know when you get that far.  

What release number are you using? (10.04 LTS, 10.10, 11.04 or whatever)

---

### Post by harimurugan on 2012-03-24
> **Bucky Ball said:**
> Not use Wubi. That is intended for installing inside Windows, not dual-booting on separate partitions. You need to download the desktop ISO, burn a CD from it and boot from the CD. When you get to the options, choose 'Try Ubuntu' (without installing) and see how you go. Let us know when you get that far.  

What release number are you using? (10.04 LTS, 10.10, 11.04 or whatever)

i have desktop iso file also.. with that only i tried installing using storage device.. i have already done "try ubuntu" its working well but my problem is when i tried to install it its not showing any options for installing in seperate partition.. its show 2 options:
1.Erase and install Ubuntu
2.Custom

when i choose custom its shows 256 GB free space(my system is 280 GB).. i already have nearly 150 GB in E: F: drives so after seeing that i dont want to proceed because it may results in loss of my data.. i think it will also erase whole RAM.. plz help me out..

---

### Post by Bucky Ball on 2012-03-24
I assume you are choosing 'Custom' and getting into Gparted. At the top right there is a drop down box. In there you probably have 'sda'. If you click the box it should show the other drive which will be 'sdb'. Then you can install to it. Separate /home partition is a good idea.

/ = 20Gb
/home = large as you like
/swap = 2Gb fine

You'll find these as defaults in the partitioning section.

---

### Post by harimurugan on 2012-03-24
> **bucky ball said:**
> not use wubi. That is intended for installing inside windows, not dual-booting on separate partitions. You need to download the desktop iso, burn a cd from it and boot from the cd. When you get to the options, choose 'try ubuntu' (without installing) and see how you go. Let us know when you get that far.  

What release number are you using? (10.04 lts, 10.10, 11.04 or whatever)

11.10

---

### Post by harimurugan on 2012-03-24
> **Bucky Ball said:**
> I assume you are choosing 'Custom' and getting into Gparted. At the top right there is a drop down box. In there you probably have 'sda'. If you click the box it should show the other drive which will be 'sdb'. Then you can install to it. Separate /home partition is a good idea.

/ = 20Gb
/home = large as you like
/swap = 2Gb fine

You'll find these as defaults in the partitioning section.

plz see the attachments..

in windows my partition and free space are:

C: 24.9GB free of 48.7GB
D: 31.2GB free of 31.2GB
E: 27.6GB free of 129GB
F: 67GB free of 79.9GB 

now tell me how to proceed.. i am in 'sda' only.. still my doubt is how it shows 256GB free space..

---

### Post by harimurugan on 2012-03-24
> **harimurugan said:**
> plz see the attachments..

in windows my partition and free space are:

C: 24.9GB free of 48.7GB
D: 31.2GB free of 31.2GB
E: 27.6GB free of 129GB
F: 67GB free of 79.9GB 

now tell me how to proceed.. i am in 'sda' only.. still my doubt is how it shows 256GB free space..

i have selected "something else" in second fig.. then only i got those other fig..

---

