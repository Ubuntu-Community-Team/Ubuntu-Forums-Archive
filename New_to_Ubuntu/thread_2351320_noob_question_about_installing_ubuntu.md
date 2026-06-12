---
title: "noob question about installing ubuntu"
date: 2017-02-02
forum: New to Ubuntu
---

### Post by mikebwriter on 2017-02-02
I have both a compressed and an extracted package of ubuntu on my flash drive.
I have an amd athlon 3.3ghz with windows 7 home premium.
I've restarted with the flash drive plugged in, but it doesn't have a boot menu.
Am I supposed to change the bios to boot from usb?
If so, how do I do that?
I want to replace windows with ubuntu.
It's an offline desktop pc but I have an online laptop (no hdmi port but I don't think that's relevant) which is how I downloaded the package.
um.. it has 4gb ram and a graphics card.
I put alot of money into it, but I wouldn't be able to get $200 for it now.
Instead of throwing it away I'm turning it into a linux computer for coding, gazebo sim, videos, music and gimp - any other suggestions?

---

### Post by TheFu on 2017-02-02
There is usually a function key to be hit at boot time to control which "legacy device" is booted. On some computers it is F10, others use F2 and others use F12.  Which it is depends on the specific BIOS used.  The manual that came with the computer or motherboard should say.

Or you can go into the BIOS and change the boot order. Put USB at the top, before any HDD.

BTW, older computers often cannot handle hidef video playback without specific GPU drivers and a GPU that can perform all the video decoding in the chips.  Any $20 GPU today will have this built-in video support, but 5 yrs ago, most GPUs did not.

---

### Post by mastablasta on 2017-02-02
you are supposed to use a program such as Linux live USB, unetbooting, start up disk creator, pendrive linux etc. to "burn" the downloade image to USB drive. but before that make sure the downloaded image is same as the one on the server you donwloaded from. here is how to do that: [SIZE=2]https://help.ubuntu.com/community/HowToMD5SUM

you can install Steam and play games on Linux. many games form GOG site will work in Linux using wine (or playonlinux).

[/SIZE]

---

### Post by jv10 on 2017-02-02
Hello Mike,

Have you downloaded Ubuntu from the [website]("https://www.ubuntu.com/download/desktop")? 

If so you should be getting a .ISO file. 
You can't just copy an ISO file to a USB drive it won't execute. (for your knowledge think that an.ISO file is like a .ZIP file. You need a program like WinRAR to open whatever is inside.)

What you need to do is "extract" the ISO file into your USB. So run a program like [Rufus]("https://rufus.akeo.ie/"), Rufus will allow you to extract the ISO file direct to the USB flash drive. (Easily done choose the image and choose the USB flash drive).

After that, you should have your Ubuntu ready to go.

Simply restart your computer, and you will then need to enter BIOS to boot your computer from the USB flash drive.As said above
> **TheFu said:**
> (...) you can go into the BIOS and change the boot order. Put USB at the top, before any HDD.(...)

In order to do so just press your manufacture keys, most commons are F2, F10, F12 or DEL. Just spam press once the computer starts to go to the option that says "Boot" and simply change the boot priority to your USB flash drive. After that exit BIOS with Save and Restart. and you should see Ubuntu.

If you need anything please let us know.

---

### Post by TheFu on 2017-02-02
Ah - both the other posters, mastablasta and jv10 are correct about needing to place the ISO onto your flash drive in the correct way.  Most people use tools for that - their lists are all ones that I've heard. On Windows, I use **yumi** - it has never failed me.  OTOH, if you have an Ubuntu ISO, then you can just shove the bits starting at 0,0 onto an empty flash drive and boot it.  That has worked for at least the last 4 yrs for non-UEFI booting. I don't know anything about UEFI booting, it might work there too.  For shoving bits onto a flash drive, I use **dd** or **ddrescue**.  It is a blunt tool that assumes you know what you are doing. As such, it is possible to do bad things accidentally when using it.  There is a front-end to dd called **mkusb** that makes shoveling these bits a tad safer.  Anyway, google will find example uses and manpages for using those tools.  Since your computer is different from ours, I don't think it wise for me to provide a quick example dd command. Wouldn't want to be the guy that wiped your PC.  Just be very careful entering the devices, if you use dd or any programs like it.

That warning applies to yumi, unetbooten and all the other tools as well. Underneath, they are all just shoveling bits and we hope they go to where you intend (so be very certain that your intention is actually what you tell the computer to do).

---

### Post by Geoffrey_Arndt on 2017-02-02
Suggest you consider the "Etcher" program . . . a newer and user friendly graphical program to create a boot-able usb flash-drive (aka thumb drive, pen drive).   I've found some of the other mentioned programs to be unreliable especially "unetbootin".

Here is where to get Etcher:   [https://etcher.io/](https://etcher.io/)

IF you have a PC from about 2010-2011 or newer, you may also want to simplify your Ubuntu install by going into the bios and enabling "Legacy" mode for the PC.    That will disable UEFI and secure boot, which are not essential if you are running Linux only.    The install is much cleaner, and there is no loss of functionality.    

So, to sum up:

1).   Enable full Legacy mode in the firmware/BIOS,

2).   Change your boot order to enable usb flash-stick boot.   Often, that is a USB option re the choices, but sometimes it is identified as a second hdd.   So a bit of trial may be needed.

3).   Note what key is used to invoke/display the one-time pre-boot menu screen, . . which shows the devices and options you have to boot into.  As stated previously in this thread, it is often F12, F10 or F2.

Note:   when you do the actual install from the Live media (usb-stick) - use the option to erase the whole drive and install Ubuntu.   Very easy install.   Be sure the Grub bootloader is saved to "sda" versus "sda1" (sda is the default - - so just accept that).

Good Luck!

---

### Post by mikebwriter on 2017-02-02
thanks guys! I will have another go at it, re: your advice, today. I'll get back to you about how it goes.


- update: I've loaded the ubuntu iso image onto the flash drive. Just waiting for the AMD forum to tell me how to get to the Bios menu.

---

### Post by mastablasta on 2017-02-03
information on how to enter the BIOS is found in the motherboard manual. these should come alongn with computer. if not they are often available online. oyu just need th emodel of the motherboard. a free program called speccy will provide such information in Windows. if you already opened the PC then the model is written on the motherboard. type that into Google, add manual and you Will find it. download it and inside it  Will be detailed description on how you enter into BIOS as well as BIOS instructions. 

usually it is F2 or Delete or F10 or F11.

this informaiton (how to get into BIOS) is also usually displayed immediatelly on boot (at top left or at the very bottom of the screen). although it might not be easilly visible if the PC boots fast.

---

### Post by mikebwriter on 2017-02-03
yea finally worked with F2 repeatedly after escaping out of the boot menu.

---

