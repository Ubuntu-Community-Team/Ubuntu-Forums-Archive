---
title: "I dont understand the grub"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by grüner pfirsich on 2008-06-15
hi,

I am new with linux since one week ago. (it has been almost fine everything, i only have some problems with the audio, maybe the driver doesnt work) Aynway, my problem is with the grub.. I have windows xp sharing the hard disk with linux and my windows was working perfectly after the linux installation but when I wanted to started it later it didnt work

I have been reading how to configure the grub but I think i haven understood properly because my windows still doenst work.. I mean I can not access to the operative systems without the recovery cd.

The configuration of the grub is this:
Title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=87d23cb1-dad8-4991-baf0-ef58ad573ee6 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Microsoft Windows XP Home Edition
root (hd0,1)
chainload +1
savedefault
makeactive


I dont see anything wrong there but I am knew.. so please help me, if everyone realizes the mistake i would be glad to know it

thanx

---

### Post by ChompTheMan on 2008-06-15
Change *chainload +1* to *chainloader +1* like so:

```
title Microsoft Windows XP Home Edition
root (hd0,1)
chainload**er** +1
savedefault
makeactive
```

---

### Post by sailor2001 on 2008-06-15
when you boot up, count down every line in the boot starting with ubuntu generic as zero (0) to your windows bootloader..remember that number.  In the terminal in ubuntu type: gksudo gedit /boot/grub/menu.lst

In the first section it lists your default boot as 0 ....that is the ubuntu boot..  change that number to your windows bootloader number and click "save"

---

### Post by kansasnoob on 2008-06-15
I think you just need to change hd0.1 to hd0.0 BUT I"M NOT SURE!

Wait a bit. Many people here know how to fix that.

Just wait until you hear from someone with a great bean-count!

---

### Post by unutbu on 2008-06-15
One obvious problem with this menu.lst is that it is trying to boot Windows from the second partition of your primary hard drive, and also booting Ubuntu from the same place. Since Ubuntu is working, it's the Windows "root (hd0,1)" line that needs to change, probably to "root (hd0,0)" (i.e. the first partition of the primary hard drive). 

> **grüner pfirsich said:**
> 
Title Ubuntu 8.04, kernel 2.6.24-18-generic
root **(hd0,1)**
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=87d23cb1-dad8-4991-baf0-ef58ad573ee6 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Microsoft Windows XP Home Edition
root **(hd0,1)**
chainload +1
savedefault
makeactive

If that doesn't work, please post```

sudo fdisk -l
```

---

### Post by meierfra. on 2008-06-15
Well, the "chainload" definitely has to be "chainloader". The "root (hd0,1)"  is also definitely wrong and probably has to be "(hd0,0)".So try


title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

If this does not work, open  a terminal and post the output of 

```
sudo fdisk -l
```
(l is  lowercase L)

---

