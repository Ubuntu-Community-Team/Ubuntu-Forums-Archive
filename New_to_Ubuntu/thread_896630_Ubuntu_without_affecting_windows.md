---
title: "Ubuntu without affecting windows"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by andrewcmcardle on 2008-08-21
Hi. I have a dell laptop running vista. I also want to run ubuntu but for several reasons i don't want to repartition my harddrive. Is there any way to run ubuntu where you can save changes (unlike live cd) but not have to repartition the harddrive. I have a USB drive and i wondered if it was possible to install ubuntu to it? Thanks for any help

---

### Post by Het Irv on 2008-08-21
I think there is a way to use a USB Drive, but I have never tried it.  But there are two options for installing Ubuntu without repartitioning Windows, which one is best depends on how much you plan to use it.

1. Virtual Machine:  If you only want to run it everynow and then, with only small things open you can try this.  I would suggest VM Ware's free Virtual Server program.

2. Wubi :  Wubi creates a large file, that is formatted as ext3, and that becomes Ubuntu's hard drive, this is done without partitioning, and you will not lose any data from windows.

I would use a VM if you arn't gonna be using it much, because it has to run on top of Windows.  I would suggest Wubi if you want something more like a real install.

---

### Post by rache1111 on 2008-08-21
check out Wubi
[http://wubi-installer.org/](http://wubi-installer.org/)

its exactly what you need

---

### Post by Orwell on 2008-08-21
You could try installing Ubuntu using the WUBI installer. Simply insert the disc whilst running Windows and select, "install inside Windows". You will be asked to allocate an amount of space for the install etc etc.

After you've set it up, you will be given the option of Windows or Ubuntu each time you boot. If you choose to uninstall Ubuntu for any reason, it's a simple matter of control panel/add-remove programs.

Installing using this method, whilst not as good as a full install, does allow you the freedom of being able to save changes you make etc. Definitely a good way to 'try before you buy' :)

---

### Post by LowSky on 2008-08-21
Installing to USB works fine, I've done it before.

---

### Post by Het Irv on 2008-08-21
> **LowSky said:**
> Installing to USB works fine, I've done it before.
Do you have a link to a walkthough or a guide for installing to a USB drive?

---

### Post by pi.boy.travis on 2008-08-21
I wouldn't recommend using Wubi for anything other than trying out Ubuntu.  I Have had several bad experiences with it.  If you back everything up, and make sure you have a Windows CD just in case, it is very safe to partition your hard drive.  The Ubuntu installer makes it amazingly easy.

---

