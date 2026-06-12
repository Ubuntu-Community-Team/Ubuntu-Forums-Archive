---
title: "Ubuntu 12.10 not booting"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by PraveenP on 2012-11-08
Hi, I downloaded 12.10 image and tried to boot from it. But whenever I try (irrespective of medium DVD/USB), it shows a message "secure boot not enabled" and screen blanks. I waited more than 10 minutes hoping it would switch to some second handler if any. But it didn't. :(

My machine is Lenovo Ideapad Z570, and it has no option to enable or disable UEFI. Please Help. Ubuntu 12.04, Mint Maya are working fine.

---

### Post by alkh3myst on 2012-11-08
Hi, PraveenP. Did you use Startup Disk Creator to ensure making your CD/USB bootable? The image file alone can't boot your system. If you're already well aware of this, my apologies.

---

### Post by newb85 on 2012-11-08
I have no experience with Secure Boot, but here's what I've gleaned from a little net searching:

Secure Boot is a feature Microsoft requires all manufactures shipping their products with Win8 to put on their machines.  It's designed to prevent a modified OS from booting, but has the side effect (or intended effect?) of preventing an alternative OS from being enabled.

I believe there should be a way to disable this in your BIOS, but as I said, I'm not familiar with Secure Boot.

Unfortunately, community support for Secure Boot is still somewhat lacking, as machines shipping with Win8 are still a relatively new phenomenon.

You may want to have a gander at this thread
[http://ubuntuforums.org/showthread.php?t=2081670](http://ubuntuforums.org/showthread.php?t=2081670)

---

### Post by PraveenP on 2012-11-08
> **alkh3myst said:**
> Hi, PraveenP. Did you use Startup Disk Creator  to ensure making your CD/USB bootable? The image file alone can't boot  your system. If you're already well aware of this, my apologies.

No, I am not. I remember old versions' images are bootable. I was able to directly reach live session from booting CD. I created my USB by UNetBootin. It is well capable of making bootable drives. I did create bootable drives for even Core plus and puppy using that software. More than that, if bios cannot find a bootable medium, it will display an error showing that. Here the error message is "Secure boot not enabled".


> **newb85 said:**
> 
I believe there should be a way to disable this in your BIOS, but as I said, I'm not familiar with Secure Boot.

Unfortunately, community support for Secure Boot is still somewhat  lacking, as machines shipping with Win8 are still a relatively new  phenomenon.

I think my BIOS is also not familiar with Secure Boot. And also it is not a windows 8 pc, I bought it in March, before this secure boot crap era. :(

---

### Post by grahammechanical on 2012-11-08
Hi,

I would not be surprised if Secure Boot capable hardware was being sold before windows 8 was released.

Ubuntu 12.10 is the first Linux distribution that should install on a Secure Boot motherboard. This blog post might not make things any clearer. You should be able to install 12.10 without Secure Boot enabled.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Does the installer give you an option to use UEFI or BIOS?

Another thought has just entered my head. Perhaps this error message is nothing to do with the problem. 12.10 must check and report if Secure Boot is enabled or not. Perhaps the issue of the blank screen is to do with the video card.

You could try running the DVD with the nomodeset option selected.

Regards.

---

### Post by newb85 on 2012-11-08
> **grahammechanical said:**
> Another thought has just entered my head. Perhaps this error message is nothing to do with the problem. 12.10 must check and report if Secure Boot is enabled or not. Perhaps the issue of the blank screen is to do with the video card.

I think you're right.  Having not yet installed 12.10, I didn't know it would report whether secure boot was enabled on the hardware.

---

### Post by PraveenP on 2012-11-08
> **grahammechanical said:**
> Hi,

I would not be surprised if Secure Boot capable hardware was being sold before windows 8 was released.

Does the installer give you an option to use UEFI or BIOS?

It looks like my laptop machine is not Secure Boot capable. I cannot find an option to use UEFI or BIOS.


> **grahammechanical said:**
> Another thought has just entered my head. Perhaps this error message is nothing to do with the problem. 12.10 must check and report if Secure Boot is enabled or not. Perhaps the issue of the blank screen is to do with the video card.

You could try running the DVD with the nomodeset option selected.

It has optimus. I tried both options "Optimus" and "UMA only". Failed. 

Grub to is not loading (or not visible), so I am not able to add nomodeset there. :(

---

### Post by newb85 on 2012-11-08
Press any key when you see the little man and keyboard, then press F6, and select nomodeset from the list, and continue booting.

---

### Post by PraveenP on 2012-11-08
It shows the earlier said message only.

---

### Post by PraveenP on 2012-11-08
Hey! I did boot from USB drive. Just opened the USB medium from existing installation. And edited 
/boot/grub/grub.cfg

removed ```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi
```part.

From rebooting from USB medium, it simply loaded. :-) Thanks for the grub hints :guitar:

---

### Post by Lupajz on 2012-11-11
Hey, I have z570 myself, had this issue on 12.04 instalation becouse grub menu was not showing :) 
[http://jacobfogg.blogspot.sk/2012/01/installing-ubuntu-1110-on-lenovo-z570.html](http://jacobfogg.blogspot.sk/2012/01/installing-ubuntu-1110-on-lenovo-z570.html) I only followed this tutorial and It worked :) 

After that I updated my BIOS from Lenovo site and did the clean install of 12.10 without any problems :)

---

### Post by PraveenP on 2012-11-11
I have no such problem while I tried 12.04. If I remember correctly, only problem I faced was related to Optimus. It was fairly simple to boot from 12.04 CD.  :-/

Later I switched to Mint Maya, just for the Interface. :-) I probably will not install 12.10 or Mint 14 in this computer (Which is my primary machine), because Maya is working well and LTS. But I couldn't help myself from testing 12.10.  As I said, I was able to boot from USB drive by editing grub.cfg, but I think this will help any others facing same problem.

---

### Post by Lupajz on 2012-12-29
Well this is funny situation I have experienced :P I have been running dual-boot W7 and Ubuntu 12.10 **32-bit** since early november haven't experienced single problem, but 2 days I downloaded my new Windows 8 Proffesional 64b ISO from DreamSpark and just for curiosity have tried it in VB on Windows 7 :P 

After that I decided to go for a Mint 14 64bit version, so I have created myself an USB with image, but I started getting this Secure boot message :P strange ... but removing those lines from USB made me boot into Live session and get it to install :P but after installation the grub was corruputed so I had to repair it :) took some time but works now.

---

### Post by bodueko on 2012-12-29
You are using an EFI enabled bios laptop... The problem is your bios.
Put in the disc and boot the laptop
Immediately the screen has backlit before it displays anything keep tapping F2
Navigate the tabs till you see override boot and select the medium of the ubuntu disc
This is with the assumption obviously that secure boot is turned off - You can double check that

---

