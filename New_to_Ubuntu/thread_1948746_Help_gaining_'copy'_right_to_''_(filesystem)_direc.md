---
title: "Help gaining 'copy' right to '/' (filesystem) directory to install Win7 from Ubuntu"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by VpNKBQLjz0 on 2012-03-28
Hey guys. Trying to follow this guide and I really need some help:

[http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc](http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc)

My internal disc drive is broken. I cannot boot my laptop from a USB. Been trying for about 4 days now and I always get the 0xc000000e error upon booting from Usb. Sometimes it just sits at the flashing cursor forever. Also I have no expensive external drive... :/ seems like my old Laptop just can't boot from Usb either. Funny how it could to install Ubuntu though.

So point is. The guide says that I need to copy the downloaded grub4dos 'grub.exe' file to the '/' directory of my Ubuntu installation. Problem is you can't copy anything there, and to my knowledge taking ownership of that directory bricks your Ubuntu installation. So how do I copy the grub.exe there so I can continue the guide?

Or does anyone else have an easier way of being able to run a Windows setup that will install properly without having to boot from a Usb or Dvd?

Thanks a lot for any and all help!

---

### Post by oldfred on 2012-03-29
You have to use sudo to have admin rights to do anything in /. But you have to be careful not to damage system or you may not be able to boot at all. And if you cannot boot a CD or USB you end up with a nice doorstop.

You also have to boot from a CD or USB to repartition. You cannot use gparted while running Ubuntu on the same partition.

Windows will only install to a primary NTFS formated partition with the boot flag. Windows 7 typically needs a minimum  of 30GB, but may work in less but will fill up and slow down quickly.

---

### Post by Mark Phelps on 2012-03-29
> **Leijonasisu said:**
> ... My internal disc drive is broken. 

So, how exactly, do you plan to install Win7 if your drive is broken?

---

