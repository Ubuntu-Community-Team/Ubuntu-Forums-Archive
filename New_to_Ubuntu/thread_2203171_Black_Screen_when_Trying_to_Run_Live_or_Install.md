---
title: "Black Screen when Trying to Run Live or Install"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by Zythyr on 2014-02-02
I have a Lenovo Ideapad Z510 laptop. 

I created a USB installer for Ubuntu 13.10 Desktop and booted using the USB. 

I get a black screen after selecting "try without installing" or even when I choose "install ubuntu". Only way I can get it work is when I choose "*acpi=off*". 

Why is this happening? Does this mean my laptop is not compatible with Ubuntu? 

Also, when I am running on Live mode (*try without installing*), the Wifi doesn't work. I have to connect using Ethernet. My wireless card is Boardcom BCM43142 (14E4:4365).

---

### Post by oldfred on 2014-02-02
Intel has been offering updates to Linux for kernel, support software & video driver. But even more improvements should be in 14.04 as Haswell's are very new and it usually takes a while for Linux to catch up as vendors often do not help much and lead time to get changes into distributions.

Many Intel video laptops need this as boot parameters.
 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor

And Dell says this issue is common to many Intel systems.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

     

> Since these are Haswell systems, if you're running Ubuntu, you'll want to run Ubuntu 13.10--at least until Ubuntu 12.04.4 is released in January. Ubuntu 12.04.3  and 13.04 don't have support for the Haswell Intel Wireless chipset in  these systems. Depending on which configuration you have, you may need  to specify the nomodeset boot option if you're going with Ubuntu 12.04.3  or 13.04. 

 

> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.

And 12.04.4 has been delayed for a couple of weeks.

---

