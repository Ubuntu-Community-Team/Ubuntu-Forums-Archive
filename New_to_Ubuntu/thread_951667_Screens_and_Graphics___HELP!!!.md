---
title: "???Screens and Graphics???   HELP!!!"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by naknak987 on 2008-10-18
Ubuntu 8.04

Hello, Just reinstalled 8.04 on my system and after installation I set up my nvidia driver with envyng. After it reboots and I change the resolution to 1024x768 (max for monitor (hp pavilion mx50)) 60hz, then logout and log back in, I get these barely visible lines waving around the screen. That happened last time I installed but I can't remember how I fixed that. I know I was in the screens and graphics thingy under applications>Other (not there by default, but can be put there in some menu editor thing.) Well, I can't get it to work. Any suggestions? 

I looked and searched the forum but I couldn't find anything thats really related to my problem.

---

### Post by overdrank on 2008-10-18
> **naknak987 said:**
> Ubuntu 8.04

Hello, Just reinstalled 8.04 on my system and after installation I set up my nvidia driver with envyng. After it reboots and I change the resolution to 1024x768 (max for monitor (hp pavilion mx50)) 60hz, then logout and log back in, I get these barely visible lines waving around the screen. That happened last time I installed but I can't remember how I fixed that. I know I was in the screens and graphics thingy under applications>Other (not there by default, but can be put there in some menu editor thing.) Well, I can't get it to work. Any suggestions? 

I looked and searched the forum but I couldn't find anything thats really related to my problem.

Hi and have you tried the nvidia-settings also :)

---

### Post by naknak987 on 2008-10-18
I still can't get those lines to go away, maybe I'm not messing with the right settings?

---

### Post by naknak987 on 2008-10-18
*bumb*  


I think its because the horizontal line frequency and the vertical raster frequency are wrong, my monitor is rated for 30-54 kHz and 47-100 Hz. I dont know how to change that tho?

---

### Post by eternalnewbee on 2008-10-18
> **naknak987 said:**
> *bumb*  


I think its because the horizontal line frequency and the vertical raster frequency are wrong, my monitor is rated for 30-54 kHz and 47-100 Hz. I dont know how to change that tho?

Is your Hardware Driver enabled?

---

### Post by naknak987 on 2008-10-18
I enabled the hardware driver for my video card but nothing else

---

### Post by eternalnewbee on 2008-10-18
> **naknak987 said:**
> I enabled the hardware driver for my video card but nothing else

What kind of graphic card do you have? ( please don't say it's ATI... )

---

### Post by naknak987 on 2008-10-18
nVidia 128mb, I don't know exact model or anything, it on board. I used envyng to install drivers.

---

### Post by stephanvaningen on 2008-10-18
overdrank mentioned the nvidia-settings: did you check? You can check by:
```
sudo apt-get install nvidia-settings
```
then run:
```
nvidia-settings
```

---

### Post by naknak987 on 2008-10-18
yea, I played with that for a while and couldn't find any settings that made a difference.

---

### Post by naknak987 on 2008-10-19
*bumb*

---

### Post by eternalnewbee on 2008-10-19
> **naknak987 said:**
> *bumb*

In Main Menu > System > Preferences > Appearance > Visual Effects, see which one is enabled. If other than none, try to set it none, and see if that solves anything.

---

### Post by northern lights on 2008-10-19
Can you please post the output of ```
sudo lshw -C display
```Thank you.

---

### Post by naknak987 on 2008-10-19
*-display               
       description: VGA compatible controller
       product: C51PV [GeForce 6150]
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by northern lights on 2008-10-19
Does 'nvidia-xconfig' solve anything?

Run```
sudo apt-get update && sudo apt-get install nvidia-xconfig
```subsequently, execute```
nvidia-xconfig
```Should you still not get higher resolution, completely reset X with```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by naknak987 on 2008-10-19
Ok, I tryed that and it did't help. remember I have the resolution i want. But I can see those lines that run up your screen that your not supposed to beable to see.

---

