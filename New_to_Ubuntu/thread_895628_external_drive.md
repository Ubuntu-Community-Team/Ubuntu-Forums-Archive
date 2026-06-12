---
title: "external drive"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by patchido on 2008-08-20
if i have a dell inspiron 1420 and want to install LTS in a sata ext HDD will it modify anything on my laptop... i dont even want to have grub on my laptop.... i just want it in the ext HDD... is it possible?

---

### Post by bobnutfield on 2008-08-20
Yes, it is possible and you can install grub to the usb drive only to boot Ubuntu.  Your laptop must be capable of booting from USB.

---

### Post by patchido on 2008-08-20
well.. is there any kind of walkthorugh the installation procces so that grub wont install into my laptop?

---

### Post by Gannon8 on 2008-08-20
Just install as normal, but selecting the USB drive. At the end, where theres a summary of changes, there should be a button that says "Advanced" or something like that. Click on it, then where it says "Install bootloader" or something like that, choose your drive instead of the default.

---

### Post by patchido on 2008-08-26
well...... something really strange happend... i installed it succesfully and when i runned i booted from ext HDD and grub did appear... but then none of the ubuntus worked... not even the other os's that appeared.... any suggestion??? i dont remeber what the warning said... it said something about not finding something

---

### Post by aninaiian on 2008-08-26
It's probably not working because you changed the boot order to allow for booting to the usb hard drive.  What you probably have to do is edit the line (hd x,x) to (hd 0,0) assuming you changed the boot order such that you boot from the usb drive first.

To do so, just reboot when it shows the grub menu (where you can choose what OS to boot) hit esc.  Then select the kernel you wish to boot and hit 'e' to edit it.

On the first line 'root (hdx,x)' hit 'e' again and change it to 'root (hd0,0)'
Hit enter and then press 'b' to boot if all when well you should boot from the usb drive.

If it worked, then just change the same line in the file /boot/grub/menu.lst.

---

### Post by patchido on 2008-08-26
thanks a lot :P really helkped me :D

---

