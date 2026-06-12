---
title: "Does the Lenovo X380 Yoga Pen Work With Linux/Ubuntu?"
date: 2023-07-26
forum: New to Ubuntu
---

### Post by gtkhead on 2023-07-26
Hi all,
I just bought a refurbished Lenovo X380 Yoga with ThinkPad Pen and touch-screen. Before I wipe out the Windows 10 Pro installation, I'd like to find out if Linux will recognize and work properly with the system, especially the pen, the pen charger, and the touchscreen. Here are my questions regarding this:

1) Does anyone on here have first-hand experience with this machine and Linux?
2) Does Linux Live find all the hardware?

Other questions:
3) Can I control my Canon EOS Rebet T2i camera for:
[LIST]
[*=1]previewing, 
[*=1]focusing, 
[*=1] framing, 
[*=1]shooting, 
[*=1]transferring images? 
[/LIST]
4) I'd like to use it as an ebook reader as well, but is there an app for dimming the screen? Not a dark mode (because I have a condition that causes physical pain when I try to read light coloured text on a black background) but a way to actually dim/brighten the entire screen?

Thanks.

---

### Post by grahammechanical on 2023-07-26
> 2) Does Linux Live find all the hardware?

Try the live session and see if everything works. That is the recommended method. That is the reason for the Live/Try session's existence.

Edit: And then there is this

[https://pcsupport.lenovo.com/gb/en/products/laptops-and-netbooks/thinkpad-x-series-laptops/thinkpad-x380-yoga/solutions/pd031426-linux-for-personal-systems](https://pcsupport.lenovo.com/gb/en/products/laptops-and-netbooks/thinkpad-x-series-laptops/thinkpad-x380-yoga/solutions/pd031426-linux-for-personal-systems)

If there are drivers available and repository you can add to the sources.list text file, you can then install Synaptic Package Manager and search for any Lenovo drivers and Synaptic will install them.

Regards

---

### Post by MAFoElffen on 2023-07-28
There are Lenovo specific drivers in this repo... :
[http://lenovo.archive.canonical.com/](http://lenovo.archive.canonical.com/)

But it is divided into a lot of sub-sections. You may have to contact Lenovo Support to see which sub-section is for your device. They also have a lot of Pub's for installing Linux on their devices. 
Examples: 
[https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf), 
[https://download.lenovo.com/pccbbs/thinkcentre_pdf/ts_p3_ubuntu_linux_22.04_lts_installation_v1.0.pdf](https://download.lenovo.com/pccbbs/thinkcentre_pdf/ts_p3_ubuntu_linux_22.04_lts_installation_v1.0.pdf),
[https://download.lenovo.com/pccbbs/mobiles_pdf/lenovo_bios_setup_linux_wmi_sysfs_1.2.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/lenovo_bios_setup_linux_wmi_sysfs_1.2.pdf)

As a Certified Lenovo, HP and Dell Onsite Warranty Tech, I was surprised that all 3 had so much, but that their own normal channel tier support techs had no idea they they even supported anything except Windows. 

Happy hunting.

---

### Post by #&amp;thj^% on 2023-07-28
All good information above, They use a Wacom AES digitiser, there will be many third party pens about that will work. There are entire review sites dedicated to testing out the different kinds of stylus pens on offer, I suggest taking a look around.

---

