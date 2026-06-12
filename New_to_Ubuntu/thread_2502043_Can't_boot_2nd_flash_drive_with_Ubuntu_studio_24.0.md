---
title: "Can't boot 2nd flash drive with Ubuntu studio 24.04"
date: 2024-10-30
forum: New to Ubuntu
---

### Post by planemad on 2024-10-30
Hi. I've managed to install Ubuntu studio to a 2nd 128gb Kingston drive(ext4). 
(the drive doesnt show in windows 10 file manager, but it shows in devices attached)
I can't boot into it to start Ubuntu. 
I can boot into the  installation drive and can open dolphin and see the files in the 2nd drive. Any suggestions would be great. 
.Thank you.

---

### Post by planemad on 2024-10-30
here are the files in my 2nd flash drive

---

### Post by tea for one on 2024-10-31
> **planemad said:**
> I can boot into the  installation drive and can open dolphin and see the files in the 2nd drive.
While you are using the installation drive, open a terminal and enter:-
```
sudo parted -l
```
Please post the command and output within code tags.

---

### Post by grahammechanical on 2024-10-31
Have you gone into the UEFI settings and selected the 128 GB drive? It sounds to me that the motherboard is still set to have the Windows drive as the drive to boot from. You need to give the Ubuntu drive the boot priority. The Ubuntu boot loader (Grub) is able to detect Windows boot files and offer an option to boot Windows from the Grub boot menu.

Regards

---

### Post by yancek on 2024-10-31
> (the drive doesnt show in windows 10 file manager, but it shows in devices attached) 

That is expected behavior as historically, windows systems do not read or write to Linux filesystem although LInux partitions will be see in tools such as Disk Management.  The most likely solution is to change the boot order in the BIOS boot options suggested above and if that  fails, post the output of the command suggested in post 3.

---

### Post by planemad on 2024-11-01
progress kind of. Ive tried installation to surface pro 5 and dell xps 5930, and both laptops, i cant seem to get past this line ....  (see attachment) ..if anyone know why? thank you

---

