---
title: "Displaced screen during installation"
date: 2018-03-22
forum: New to Ubuntu
---

### Post by daveriz on 2018-03-22
After I start the laptop and pass the BIOS screen etc (which looks perfect) and Ubuntu installation initiates from them USB stick I get displaced large screen and not able to install.
Artifacts and garble allover the screen.
I tried Neon KDE, Kubuntu and last regular "ubuntu-16.04.4-desktop-amd64" with same results.

BIOS and first starting screen is ok.

[https://cl.ly/3o1I2x3p1G0t/IMG_0391%201%201.jpg](https://cl.ly/3o1I2x3p1G0t/IMG_0391%201%201.jpg)

**[SIZE=4]As soon as installation selection starts the screen goes crazy, displaces and shows multiple copies of itself.:confused:[/SIZE]**

[https://cl.ly/0y1A0D2H331P/IMG_0390%201%201.jpg](https://cl.ly/0y1A0D2H331P/IMG_0390%201%201.jpg)

Laptop specs


[TABLE="class: table table-bordered table-steps"]
[TR]
[TD="align: left"]2.00 GHz AMD Turion 64 X2 Dual-Core Mobile Technology TL-60
[/TD]
[/TR]
[TR]
[TD="align: left"]  **Microprocessor Cache** [/TD]
[TD="align: left"] 512 KB + 512 KB L2 Cache[/TD]
[/TR]
[TR]
[TD="align: left"]  **Memory** [/TD]
[TD="align: left"] 4 GB
[/TD]
[/TR]
[TR]
[TD="align: left"]  **Memory Max** [/TD]
[TD="align: left"] Up to 4GB DDR2 (Up to 1 GB may not be available due to 32-bit operating system resource requirements)[/TD]
[/TR]
[TR]
[TD="align: left"]  **Video Graphics** [/TD]
[TD="align: left"] NVIDIA GeForce Go 7150M[/TD]
[/TR]
[TR]
[TD="align: left"]  **Video  Memory** [/TD]
[TD="align: left"] Up to 1071 MB[/TD]
[/TR]
[TR]
[TD="align: left"]  **Hard Drive** [/TD]
[TD="align: left"] 250 GB (5400 rpm)[/TD]
[/TR]
[TR]
[TD="align: left"]  **Multimedia Drive** [/TD]
[TD="align: left"] LightScribe Super Multi 8X DVD±R/RW with Double Layer Support[/TD]
[/TR]
[TR]
[TD="align: left"]  **Display** [/TD]
[TD="align: left"] 14.1" WXGA High-Definition BrightView Widescreen Display (1280 x 800)[/TD]
[/TR]
[/TABLE]

---

### Post by ajgreeny on 2018-03-22
You probably need to boot the installation USB or DVD with the nomodeset boot option.

If using legacy BIOS, hit F6 when the first screen appears and choose from the list of options.
If using UEFI, at the grub menu where you choose either to "install" or "try without installing" choose the try option, press **e** to edit, and navigate to the line that shows **quiet splash** near the end.
Either add **nomodeset** after the quiet splash or replacing them.

Hopefully that will get you to a proper GUI desktop from where you can install the OS, then after installing you will have to install the appropriate nvidia driver after the reboot, again after using nomodeset.

See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by daveriz on 2018-03-22
Thanks, I got rid of neon kde because I dont know how to turn on nomodes with command line, whereas vanilla ubuntu has a F6 popup permade. Installing ubuntu now. I'm settling for ugly for her smarts. :mad:

---

