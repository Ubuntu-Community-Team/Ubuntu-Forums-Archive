---
title: "[SOLVED] Can't install Ubuntu :("
date: 2008-07-30
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-07-30
I have a SATA hard drive and I am trying to run Ubuntu on it. Below is a image of the error I get. I can use no hard drive or another hard drive and Ubuntu will boot. Any ideas?

---

### Post by ElephantGun on 2008-07-30
The drive may be physically broken is the only explanation I can think of.

Try downloading a diagnostic utility from the manufacturer of the drive, and use a floppy or CD to boot it in DOS... some of them have options to repair it if it's broken.

---

### Post by jamesrfla on 2008-07-30
I will try to reformat it again and see if their is something wrong with the BOIS. I will also try another SATA drive and see if it works.

---

### Post by ElephantGun on 2008-07-30
There's also the possibility that it's your ubuntu install CD, if it's scratched up you should consider burning another one. I think that's highly unlikely though.

---

### Post by jamesrfla on 2008-07-30
Yeah the CD is fine. I checked it and just burned it recently. I check the BOIS and it sees the drive fine. Maybe Ubuntu is having trouble interfacing with a SATA hard drive. I tried running Ubuntu on my desktop that I built with a SATA drive and it doesn't seem to work.

---

### Post by Rocket2DMn on 2008-07-30
I believe this is a SATA issue, possibly a problem with JMicron support.  Try booting with the "irqpoll" kernel option.  If that doesn't work, try using "acpi=off noapic nolapic" instead.

---

### Post by jamesrfla on 2008-07-30
> **Rocket2DMn said:**
> I believe this is a SATA issue, possibly a problem with JMicron support.  Try booting with the "irqpoll" kernel option.  If that doesn't work, try using "acpi=off noapic nolapic" instead.

How do you do that with the live CD? Also I tried installing XP and that didn't work. Even though I am A+ certified I can't figure this out. I have to finish working on this tommorow afternoon because ill be gone.

---

### Post by Rocket2DMn on 2008-07-30
If you press F6 at the initial screen for the LiveCD you can choose Other Options (or something similar).  There you can edit the boot line after "rw quiet splash" to add the new options.

---

### Post by jamesrfla on 2008-07-31
I am on step two of this [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
My question is there are two flavors of permanent to consider. The first is to make the change survive reboots, the second is to survive an upgrade. Which one should I pick?

---

### Post by Rocket2DMn on 2008-07-31
What is is saying is that when you edit the boot paremeters from GRUB, it does it only for that boot.  If you want to make the changes stick, you need to edit the grub configuration file - but you need to do it in the correct form to prevent the changes from being deleted when the configuration file is overwritten when new kernels are introduced and the file is regenerated.
First make a backup
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Now open to edit:
```
gksudo gedit /boot/grub/menu.lst
```
If you just add the options to each kernel manually, the changes will be deleted when the file is autoupdated later.  So rather than doing it like that, find the line that says something like 
```
# defoptions=splash quiet
```
And change it to something like
```
# defoptions=splash irqpoll
``` or using whatever parameters are necessary on your system.  Do the same for the altoptions line (for the recovery mode kernel):
```
# altoptions=(recovery mode) single
```
and change to something like
```
# altoptions=(recovery mode) single irqpoll
```
Save and close the file, now regenerate it with the new options:
```
sudo update-grub
```
Double check the file to see that the options have been added correctly, then you can reboot and the changes will automatically be added in GRUB.

---

### Post by jamesrfla on 2008-07-31
Okay that worked. With having these options enabled (acpi=off, noapic, and nolapic) do any of them change the way Ubuntu looks when it boots?

---

### Post by jamesrfla on 2008-08-05
Okay I found out that acpi=off, noapic, and nolapic don't have to do anything with the way Ubuntu looks when you boot up the live CD or boot it off the hard drive once you have it installed. Thanks for all your help!!:)

---

