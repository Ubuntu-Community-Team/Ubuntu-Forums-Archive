---
title: "The creation of swap place in partition #3 of SCSI1 (0,1,0) (sda) failed"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by kamil22 on 2015-12-31
Hello, I am not sure if this is the right place to post this but I really do need your help. I used to have Windows 10 on my HDD but lately I've been feeling like trying Ubuntu for good, and see if I can work with it. What I did was download the latest .iso for Ubuntu and then burn into a USB stick. I have then booted from the USB and tried to install Ubuntu alongside Windows 10. However, something went wrong and it failed. After that I tried to erase my HDD and install Ubuntu, however it keeps giving me this error: > The creation of swap place in partition #3 of SCSI1 (0,1,0) (sda) failed. I have then Nuked my HDD with Dban with the option quick erase and checked for any sector errors but everything is fine. Each time I try to install it it gets to the world map point and then the error appears. I have attached some photos so you can get a better idea. Any help is appreciated.

---

### Post by grahammechanical on 2015-12-31
What install option are you choosing? Is it, Erase disk and install Ubuntu? Or, Something Else?

With the Something Else option we have to specify the partition to use for Ubuntu and give it a mount point of /. And we also have to specify a partition to be used as swap and give it a mount point of swap.

If we fail to give the partitions a mount point then errors like that will appear. If we are installing Ubuntu and a partition that is already being used as swap exists then the installer will automatically recognise that particular partition as a swap partition and use it. 

Regards.

---

