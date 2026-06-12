---
title: "Wifi, PCMCIA &amp; Hair Loss"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Mr Smiler on 2012-06-26
Hi folks.

My second thread in as many days.

I have installed Ubuntu 12.04 LTS on a Dell Inspiron 8500 laptop.

I have solved the issue with the NVIDIA GeForce 4200 GPU (pixelated appearance) by searching & finding previous examples to download a driver.

All good.

Now I want to get the WiFi working.  It's not a Dell on-board item, it's a USR 54Mbps card (Windows driver is: usr11g_v6.0b15).  

The info returned from "lshw -C network" is:

product:  ACX 111 54Mbps Wireless Interface
vendor:  Texas Instruments

There is no driver associated with it.  I have downloaded the usr11g_v6.0b15.exe file & also extracted that same file on a PC running windows which extracted a folder with 2 'cab files & some others).

I need to establish a step-by-step procedure.

I have found a couple (well loads actually) but they all seem to assume that a fair amount of knowledge is already acquired.

So far, my thoughts are:

4. ndiswrapper to install driver
3. find .inf & .sys files
2. use unshield & cabextract to extract the .inf & .sys files from the "disk 1" folder (copied from the PC)
1. find a tutorial on using terminal to use unshield & cabextract

Being a total noob, it's hard-going but I 'think' I'm liking the challenge - something in my OCD region is triggered :)

Any tips or help would be greatly appreciated.

AH, it turns out the the NVIDA driver is not actually being used - I followed the instructions to run 'nvidia-xconfig' in root.  I re-booted & now the display is stuck on 800x600.  Is there a way to restore the earlier setting?

Found a process to re-set the NVIDIA :)

---

### Post by Redblade20XX on 2012-06-26
Have you taken a look here: 
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

-Red

---

