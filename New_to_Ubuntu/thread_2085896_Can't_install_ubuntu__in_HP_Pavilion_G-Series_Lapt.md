---
title: "Can't install ubuntu  in HP Pavilion G-Series Laptop"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by pupplar on 2012-11-19
I had been using Ubuntu for last few years on my Lenovo laptop without any problem but when I tried to install Ubuntu in my HP pavilion G-Series Laptop I got into problem . 

Ubuntu gets stuck at the install screen so I dont know what  the  problem is ? I really love ubuntu and dont want to leave it but somehow I am not able to install it in my HP Laptop.

---

### Post by oldfred on 2012-11-19
Welcome to the forums.

Is this a newer system with UEFI or is it UEFI but still in BIOS mode?

Post this from terminal in liveCD or USB flash drive:

       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
    
Both Winddows & Ubuntu have to be in same mode either UEFI or BIOS. Only 64 bit Ubuntu supports UEFI.

If BIOS mode you probably have the 4 partition limit.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

