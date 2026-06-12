---
title: "Ubuntu Anomaly"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by CoDeHacKer on 2012-04-26
Hi, 

I installed Ubuntu 32 bit on my wifes computer, and tried installing it on mine, and 
couldn't get it to boot afterward.  My computer is a 64 bit HP DV7 with a I7 processor
and 8 gigs of ram. This was 11.10 

I figured it must be something with the 32/64bit OS, so I started dling a 64bit 12.04.
While I was dling it for some reason I took the drive and plugged it into my wifes 
computer and it booted right up to grub.  I brought the copy I installed on her computer
and plugged it into mine and it booted up ???

I would really like to install the 64 bit os on mine now, does anybody have any Idea why 
Ubuntu hates me.   I can install it on the old 32 bit machine, and it will work on either 
computer, but it has the hardware for the other computer on it, or I can install it on 
this computer, the DV7, and it will only boot on the old computer.

I Imagine it is something in the grub, I can boot to the CD just fine, I was looking 
through the grub.cfg file and it lists HD1 MSDOS6  then HD1 MSDOS1 as the boot 
devices.  SDC1 is my /  SDC2,and3 are blank for future primary use, and SDC 5 
is Home for my music and pics, and SDC6 is usr and sdc7 is swap.  /dev/sdc is on 
a USB 3.0 SATA drive, and it is HD1.  I tried it in the 2.0 USB ports too.

Could it be something in my boot sector ?   in Gparted and in windows it says the 
1st partition starts at 2048, or is that normal.  You would think if it was something 
like that though, that it wouldn't boot in the old computer. 

Thanks

---

### Post by CoDeHacKer on 2012-04-29
I finally found what it was, it's UEFI BIOS.  I don't know why it worked before, but it won't work 
at all now.  Is there a boot loader that works with UEFI Bios, without all that you have to go 
through with grub to make it work ? 

Like something you can burn a ISO and install and it work ?   For booting a few Operating 
systems, like Dos, Windows, and Linux.  I'd even be willing to pay for it.

---

