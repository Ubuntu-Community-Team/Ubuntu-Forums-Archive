---
title: "Ubuntu wont auto boot"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by jbdevega on 2014-07-15
I installed Ubuntu recently on my computer and everything works great short of it wont auto boot into Ubuntu. If i let the computer boot on its own it just comes to a blank screen and says "NO bootable device". I can still get Unbuntu to boot if i hit esc and then tell it to boot Ubuntu while the computer is loading up. any help would be greatly appriciated as im new to Ubuntu.

Also would like to note that so far ive tried boot repair with no luck and also tried to reinstall grub unsuccessfully.
This is not a duel boot, i just have Ubuntu installed.  I also double checked the boot order, the hard drive is the first boot device.

---

### Post by nerdtron on 2014-07-15
"No bootable device" could mean a wrong boot order on the BIOS of the computer. Be sure to check it and set the Ubuntu hard drive as the first boot choice.

---

### Post by grahammechanical on 2014-07-15
When you press Esc does it offer to boot Ubuntu? Are you getting a Grub boot menu? Or is the machine offering you a selection of drives to boot from? What do you actually see when you press Esc. Knowing that will clarify things for us.

Regards.

---

### Post by jbdevega on 2014-07-15
ok so when i hit "esc"  it goes to the menu where i can select Boot Device Options (F9) or other options like the BIOS.  

I hit F9 and then it takes me to another menu with three options:
-Notebook Hard Drive (selecting this takes me to the black "no boot device screen")
-ubuntu (boots Ubuntu)
-Ubuntu (also boots Ubuntu, maybe safe mode?)

selecting either Ubuntu option takes me to another menu where i get a few seconds to select one of two options:
-Ubuntu
-Advancced Options for Ubuntu

Not sure which menu is GRUB, im thinking its the fir menu with three boot options.  either way i did double check and my hard drive is the first boot option but it just acts like nothing is there.

---

### Post by yancek on 2014-07-15
Is Ubuntu the only operating system on the computer?  The default in that case is to not display the boot menu and that can be changed.

---

### Post by jbdevega on 2014-07-16
Yes it is the only OS on the computer.  How do i fix this problem?

---

### Post by buzzingrobot on 2014-07-16
> **jbdevega said:**
> ok so when i hit "esc"  it goes to the menu where i can select Boot Device Options (F9) or other options like the BIOS.  

I hit F9 and then it takes me to another menu with three options:
-Notebook Hard Drive (selecting this takes me to the black "no boot device screen")
-ubuntu (boots Ubuntu)
-Ubuntu (also boots Ubuntu, maybe safe mode?)

selecting either Ubuntu option takes me to another menu where i get a few seconds to select one of two options:
-Ubuntu
-Advancced Options for Ubuntu

Not sure which menu is GRUB, im thinking its the fir menu with three boot options.  either way i did double check and my hard drive is the first boot option but it just acts like nothing is there.


The first menu is the BIOS menu, the second is the grub menu.

i've never seen a BIOS list an OS when it lists available drives. Is there anything unusual about the machine?

---

### Post by jbdevega on 2014-07-16
its a HP Pavilion m6-1035dx
came from the Factory with 
Microsoft Windows 7 Home Premium 64-bit Edition 
6 GB RAM  
AMD A10-4600M 2.3 GHz processor
640 GB HDD 
AMD Radeon HD 7660G

The reason im booting it with Ubuntu is because i got tired of Windows giving me issues.  last issue i had with the computer was the Windows authorization code was saying my laptop was Dell when its clearly not.  Ive heard people had issues with installing Ubuntu on Dells because of something they do on the harddrive.  I figured sense i formated the harddrive that shouldnt be a problem.

---

### Post by jbdevega on 2014-07-18
been doing a bit of research, It seems like this may be a partition issue. Any ideas on why my bios can read the partition with Ubuntu but seems like it cant read the partition with Grub.

Edit:
Maybe this will help figure out whats going on.
[[COLOR=#0072c6]http://paste.ubuntu.com/7753279/[/COLOR]]("http://paste.ubuntu.com/7753279/")

---

