---
title: "New PC Build Installation of Ubuntu Issues"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by linuxaspirer on 2011-09-24
I have built new pc, and installed linux 11.04 on it. Every thing went smoooth until I was trying to install this ATI Radeon™ HD4250 drives, when I install these driver, system does not boot with ubuntu at all.
i dont have anyother operating system. Kindly help, is there any thing I am doing wrong. Are there drivers specifically for ubuntu.

---

### Post by 2F4U on 2011-09-24
How did you install the drivers, from the restricted drivers menu? Do you get error messages printed on the screen?

---

### Post by linuxaspirer on 2011-09-24
[CENTER][LEFT][COLOR=Black]I have the following parts that I used to build the computer [/COLOR]
[COLOR=Black]
Motherboard:BIOSTAR A880G+ AM3 AMD 880G HDMI Micro ATX AMD Motherboard[/COLOR]
[COLOR=Black] 
Processor: AMD Athlon II X2 250 Regor 3.0GHz Socket AM3 65W Dual-Core Desktop Processor 

[/COLOR][COLOR=Black] Memory:CORSAIR Vengeance 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)

Storage: Seagate Hard drive with 160 GB with SATA port

Wired Keyboard HP, Wireless mouse,HDTV with HDMI port as the Monitor.

I have USB stick with ubuntu installer on it.

I was trying to install ubuntu 11.04 with USB stick.

I tried few times with full installation including checking the box for automatically installing updates, installation was unsuccessful.

So last time I tried to install with out checking the box with updates and the installation was successful.

I did not have to install any drivers for the motherboard every thing was working smooth except for video quality was not upto the par on some avi files I have and also the sound output is not great.
The video quality might be secondary to the quality of the files.
The audio output was not great.

Anyway I thought everything is working well,

When I clicked on the application and install additional drivers ATI HD 4250 driver came up, so it asked me whether I would like to install, I have installed it, after installing the driver when restarted the computer ubuntu did not boot up.

When it starting to boot up it gave 4 options as if we have dual booting system. After clicking the first option did not boot up at all.

It looks like I need to start all over again, install ubuntu operating system without the automatic updates, especially - ati radeon hd 4250 drivers.

i still have this doubt in my mind how can ubuntu recognize all the driver of the mother board???????
[/COLOR][/LEFT]
[/CENTER]

---

### Post by Mark Phelps on 2011-09-24
Does that motherboard have the ATI chip on the board? Asking because my Gigabyte motherboard has an ATI 4290HD chip on it -- and installing the drivers via the Additional Drivers option worked great!

As to your last question, it doesn't really load drivers for the motherboard; instead, while it's installing, it scans the hardware on the motherboard and connected to it -- and loads the necessary drivers.

It does NOT load the ATI drivers because they're known as restricted, meaning, you have to grant permission to load them.

---

### Post by wolfen69 on 2011-09-24
My last computer build came with integrated ATI video which I disabled, then added an Nvidia card. Nvidia generally has better drivers in linux.

---

### Post by linuxaspirer on 2011-09-24
it came in with ATI video chipset...
so what should i do now?

---

### Post by linuxaspirer on 2011-09-24
> **Mark Phelps said:**
> Does that motherboard have the ATI chip on the board? Asking because my Gigabyte motherboard has an ATI 4290HD chip on it -- and installing the drivers via the Additional Drivers option worked great!

As to your last question, it doesn't really load drivers for the motherboard; instead, while it's installing, it scans the hardware on the motherboard and connected to it -- and loads the necessary drivers.

It does NOT load the ATI drivers because they're known as restricted, meaning, you have to grant permission to load them.

i gave permission for ATI drivers, after granting permission and installing and restarting computer everything screwed up... I need to do a fresh install again.

---

