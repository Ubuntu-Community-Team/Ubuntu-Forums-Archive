---
title: "Dual boot grub menu presses 'e' automatically"
date: 2020-12-15
forum: New to Ubuntu
---

### Post by katyperry78 on 2020-12-15
Hello, 

I have some issues during start-up. 

In short: 
Since a week I have a dual boot system with Windows 10 and Ubuntu 16.04. I have no previous Linux experience, except briefly in a virtual machine. It seemed fine, but not for long. When I start up my laptop (Lenovo Thinkpad P51), it shows the grub menu to select an OS for start-up. However, somehow, the letter 'e' gets pressed automatically, and I get a screen to edit the ubuntu (that's on top in the menu) option. I can move in the menu and boot an OS by pressing escape (to back to the grub menu) and hit enter quickly, before the system automatically presses 'e' again. 

Longer:
Ubuntu worked fine if I could manage to start it up. But after a few days, parts of the screen started flickering, showing other open programs. e.g. working in Firefox, some parts of the screen showed content of other tabs. Rhythmbox also has some flickering, not just Firefox. Finding out Ubuntu was installed in UEFI and thinking Windows was installed in BIOS, I thought it could be solved by reinstalling ubuntu. After formatting the part of the drive where Ubuntu was located, I found out Windows was in UEFI already. To remove everything form the old Ubuntu, I deleted the Ubuntu option in the BIOS/start up options. Now I started to reinstall Ubuntu, again 16.04. I disabled fast start up in the windows menu, and secure boot in the BIOS menu. When the grub menu showed to choose what to do with the Ubuntu iso on the USB stick, it already started with pressing 'e' again, not solving any issues. In the few minutes I spend in the new Ubuntu, there was no screen tearing, but this was also the case in the previous installation in the beginning. 

I have tried the grub repair, here is the link: [http://paste.ubuntu.com/p/tfbZSp4tzh/](http://paste.ubuntu.com/p/tfbZSp4tzh/)
No succes with the repair. And I'm too much of a Linux noob to get something useful out of the link. 

Unplugging my external keyboard did not help, and I never have keyboard issues. 


I did notice that when I'm in the bios settings, my laptop is  constantly beeping. It is from inside the laptop, not from its speakers.  Using the key 'e' is not an option in the bios, maybe it beeps because  it is pressing a key (e) without use?

Could someone provide suggestions to solve the 'e' issue? 
And as a bonus, maybe someone knows more about the screen tearing? 

I would like to use Ubuntu for ROS for my bachelor thesis. I need to use an Microsoft Kinect, which gave trouble in a virtual machine (VMWare).

Thank you for reading. 

Kind regards,
not katy perry

---

### Post by ActionParsnip on 2020-12-15
If you open a text editor and wait do a lot of e's write out?
Tried with a different keyboard?

---

### Post by oldfred on 2020-12-15
How old is system?
The 16.04 would be ok for systems from 2014 or maybe 2015. It takes a while for new kernel & drivers that support newest hardware to be included in a distribution.
Also 16.04 will reach normal EoL - end of life in April 2021. Better to use 18.04 or 20.04 as they have newer kernel, drivers & other updates. And will be supported for a longer time.
I installed Kubuntu 20.04 in my BIOS only 2006 laptop, so newer versions, still support most older hardware. Just then a lighter weight gui normally recommended for old hardware.

What video card/chip?
Video issues often related to video driver. Some like nVidia need nVidia driver.

Have you updated UEFI to latest available?
And if SSD updated SSD firmware?

Both systems need to be in same boot mode. If Windows is UEFI, then you need Ubuntu in UEFI boot mode to avoid some of the boot issues. Also then UEFI setting needs to be UEFI, not CSM/BIOS/Legacy mode. Grub cannot switch boot mode, so if booted in BIOS mode, you have to reboot to use UEFI. 
Also Windows likes to turn fast start up back on, and then grub will not boot Windows. So if issues booting Windows from grub, check that fast start up is still off. With UEFI, you should always be able to directly boot Windows from UEFI. But best to have Windows repair/recovery flash drive, just in case.

---

### Post by katyperry78 on 2020-12-15
Thanks for the suggestions. 

@ActionParsnip: nope, unfortunately that is not the issue. 

@oldfred: 
I bought it new in 2017, might be a 2016 model. 
I installed 16.04 to make use of ROS Kinetic, some packages I would like to use were tested for Kinetic. 
Video card is an nVidia Quadro M1200. ([https://www.lenovo.com/nl/nl/laptops/thinkpad/p-series/ThinkPad-P51/p/22TP2WPWP51](https://www.lenovo.com/nl/nl/laptops/thinkpad/p-series/ThinkPad-P51/p/22TP2WPWP51)). 
I will try to update UEFI and my SSDs, don't know how but will google it. 
Both systems are now UEFI. Fast start up is still off, has not yet been changed automatically.

I have checked. I use the newest UEFI version from Lenovo. Windows says driver for ssd is up to date. I could not find to turn off UEFI fast boot, maybe I don't have it. 

I did notice that when I'm in the bios settings, my laptop is constantly beeping. It is from inside the laptop, not from its speakers. Using the key 'e' is not an option in the bios, maybe it beeps because it is pressing a key (e) without use? Updated my first post with this.

---

### Post by oldfred on 2020-12-15
Did you  install the nVidia driver for your nVidia card?
With older versions of Ubuntu you had to boot with nomodeset and then install nVidia driver from Ubuntu repository. And to get newer drivers with older Ubuntu version needed the ppa.
Newest versions of Ubuntu now offer to install nVidia driver as part of install.

#What is installed
dkms status

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Microsoft requires vendors to have Fast Boot setting in UEFI. Its to make Windows seem like it is faster booting. But once configured can make Linux quicker also.
That assumes no system changes and immediately starts to boot system. When reconfiguring it, you must have it off.
Fast boot is often so quick you do not have time to press any key to get into UEFI or UEFI boot options.
But a full "cold" boot usually does a full normal UEFI rescan of system configuration.
You have to totally remove all power, including battery, if laptop. Drain all power, by holding power switch. Then boot & press correct key to get into UEFI.

---

### Post by katyperry78 on 2020-12-18
It is working now. I don't know why, but the 'e' issue stopped appearing. I installed some driver stuff, but then my second monitor didn't work anymore. Switched back and now everything seems fine. 
Thank you for your extensive answers and have a nice Christmas.

---

