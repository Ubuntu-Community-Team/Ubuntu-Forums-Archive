---
title: "broadcom wifi and live cd"
date: 2016-02-01
forum: New to Ubuntu
---

### Post by jim Kane on 2016-02-01
does anyone know of a live Linux CD that will recognises a laptops internal broadcom wifi  

Buntu would of course load the driver during installation but 
in this instance i cant do an install just need to demonstrate Linux working

Thanks

---

### Post by stalkingwolf on 2016-02-02
usually yes.

---

### Post by jim Kane on 2016-02-02
> **stalkingwolf said:**
> usually yes.


I have tried Ubuntu, Knoppix and Mint which don’t

going to try Puppy but that has a very off putting GUI for a demonstration.

---

### Post by cariboo on 2016-02-03
Which driver does the wifi device use, b43 or bcmwl?

---

### Post by jim Kane on 2016-02-03
Hi
I cant answer that question at the moment as i don't have the laptop
but i did make a note of the device
Broadcom BCM4311 14E4:4311

---

### Post by Geoffrey_Arndt on 2016-02-03
You can make a Live USB Flash-Stick with "persistence" enabled.   That way, you can install the drivers and they will be retained upon shutdown/restart.

---

### Post by coldraven on 2016-02-04
I'm running 15.10 and have the same Broadcom chip

---

### Post by jim Kane on 2016-02-04
> **Geoffrey_Arndt said:**
> You can make a Live USB Flash-Stick with "persistence" enabled.   That way, you can install the drivers and they will be retained upon shutdown/restart.

That may be what i will have to do but i was hoping to give the laptop owner the CD/DVD after i had shown it working

---

### Post by cariboo on 2016-02-05
The STA/bcmwl driver is propitiatory,  so it won't be installed by default. You can install it after you have booted from the live CD. The packages are located in /pool/main and /pool/restricted.

To get the driver to work you need to install dkms, fakeroot and  bcmwl-kernel-source.

---

### Post by jim Kane on 2016-02-05
Im trying to do this for a very elderly person that has very little knowledge of how to operate a computer other then to turn it on and open firefox or skype they also live in a nursing home and only have access to WiFi 
to complicate things the laptop will only boot a USB stick if you
first run bios setup and alter the boot sequence which is not persistent if you later start the laptop without the usb stick 
so i cant use a live persistent usb   
 but they are capable of putting a cd in and then starting the laptop
i was hoping to let them get comfortable using Linux before 
installing it in replacement of win-xp

---

