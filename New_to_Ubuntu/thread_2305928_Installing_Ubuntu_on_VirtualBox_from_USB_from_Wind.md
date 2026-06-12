---
title: "Installing Ubuntu on VirtualBox from USB from Windows 7 Host"
date: 2015-12-10
forum: New to Ubuntu
---

### Post by jwanutt on 2015-12-10
I am trying to install Ubuntu 14.04 32 on VirtualBox (version ) from a bootable USB from Windows 7 Host.  I put ubuntu onto a bootable usb, then I used the cmd to create VMDK and change virtualbox's default installation directory.  I then chose to use an existing disk drive file and chose the vmdk.  When I start the new vm machine and I get to the 'Installation type' window I don't see any partition listed and below the 'Device for boot loaderinstallation"' I only see 'dev/sda'.  if I it and select 'Install' I get a message 'No root file system is define.  Please correct this from the partion menu'.  If I select anything in this window it seems to freezes up.  What am I missing?  

Thanks!

---

### Post by sudodus on 2015-12-10
I don't think a guest system in Virtualbox can boot from USB. But it can boot directly from an iso file in the host system. It sees the iso file as a DVD disk.

---

### Post by SeijiSensei on 2015-12-10
As sudodus says, the solution here is to put the Ubuntu ISO disk image on the host machine.  When you run the "wizard" to create a new VM, it will ask you to point to the installation image.

A VM cannot boot from a USB drive for many reasons.  The most important one is that you need to install the Extension Pack after the VM is created to access USB devices.

---

### Post by C.S.Cameron on 2015-12-10
Have you tried:

[http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/](http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/)

---

