---
title: "Error message on reboot"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Jane Redd on 2008-08-22
Help! I rebooted my computer and now Ubuntu is giving me the error message: 

error 21: selected disk does not exist   
press any key to continue...

I've press any key and it just takes me back to where I began and keeps going in circles.

I need to know how to get it going again.  Thanks!

---

### Post by bobnutfield on 2008-08-22
This is an error indicating that the partition that grub is trying to boot to either does not exist or is not formatted.  Is this a new install? Was there any change to the hard disk order and do you have more than one hard disk in your system?  There are a number of things you can do, but we first need to know the answer to these questions.

Also, when you are at the grub menu, type c to get to a grub prompt and type:

> find /boot/grub/stage1

---

### Post by Jane Redd on 2008-08-22
no, this isn't a new installation...no change to hard disk, but yes, I have two hard disks on this computer...

---

### Post by Jane Redd on 2008-08-22
I tried that prompt you gave me and this is what I got:

Error 27: Unrecognized command

---

### Post by bobnutfield on 2008-08-22
OK, when you first start up, quick press the esc key to bring up the menu of boot choices.  Then, highlight your Ubuntu line and press the e key.  This allows editing of the boot line, but there is also a set of options at the top of the screen, and I believe one of them is to press the c key to bring up a grub prompt which would look like this:

> grub>

At that prompt, type the find /boot/grub/stage1 command.  This is to see if the boot directory of Ubuntu can be found.

---

