---
title: "need help booting from usb"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by ak47jx on 2014-05-27
so here is my story:
so my laptop was running windows 7 and i installed ubuntu using a usb which i totally removed windows 7. So currently my laptop is running ubuntu only. So now i decided that i want to install windows 7 back again so i made a bootable usb using unetbootin and i boot the laptop and select boot from usb but the only thing that happens is it just refreshes the select what you want to boot from screen.

can someone help please

---

### Post by cariboo on 2014-05-28
I've haven't found a reliable way to create a Windows bootable usb drive in Ubuntu either, if your system has the resources why not try Virtual Box, it's in the repositories. I build my current system to play with virtualization, and have Utropic Unicorn (14.10) versions of Gnome-shell, Kubuntu,Lubuntu and Xubuntu as well as WIndows 7 and 8.1 running like they would natively

---

### Post by sudodus on 2014-05-28
If you have a Windows 7 DVD disk, it should be possible to make an image of it to a USB pendrive or in two steps: make an iso file, and from the iso file flash the system into a USB pendrive. But the idea of Windows in VirtualBox is good, if your computer has enough horsepower and memory. Please tell us about your computer specifications :-)

---

### Post by nerdtron on 2014-05-28
You can also create a bootable windows 7 usb if you have an iso and you use the Windows 7 DVD tool from microsoft website.
Once you create a bootable windows 7 installer, you can start installing windows again. But be aware that windows will destroy grub and you should install it again if you want to boot linux.

---

### Post by ritwikraghav14 on 2014-05-29
Check out here:
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Had you followed these steps..

---

### Post by jakke1975 on 2014-05-29
If the previous answers didn't help and you still have access to a Windows machine, try this: [http://pcsupport.about.com/od/windows-8/a/install-windows-8-usb.htm](http://pcsupport.about.com/od/windows-8/a/install-windows-8-usb.htm). This works for Win8, Win7 and Vista btw, not just 8 like the url says.

I've always had trouble as well with unetbootin, it's definitely not user friendly :)

---

### Post by deAthbLisS on 2014-05-29
You can try this Universal USB installer: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) 
First Select the distribution and then browse and select the iso file.
hit create when ready. 

it supports many distributions including Win7 and Win8

---

