---
title: "Black Screen on Startup"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Mordorg on 2008-11-06
I'm trying to install Ubuntu on a old pc.

When I try to load Ubuntu I get a blank black screen. The live CD will work if I set graphics to safe mode, and turn asci:off. Which I then used to install from. I'm new to Linux and have no idea how to get it to load.

The hardware is

Asus P4C800 Deluxe (Intel 875P)
2.6 Ghh P4 (Northwood)
ATI X800XT AIW
Create X-FI Xtreme Music
1 GB Ram

---

### Post by bscbrit on 2008-11-06
I wouldn't call a P4 2.6GHz old!  I am using a 350Mhz box as a server LOL!

I'm not quite sure of the fault.  Are you saying that you have already installed Ubuntu but it will not boot at all, or that once you have passed the Grub menu the display fails?  What exactly do you see during the boot sequence?  Bios, Grub, splash screen, log on?

If my questions do not even make sense to you, let me know and I will rephrase them.  You might be new to Linux but understand computers very well, or the terminology might as well be a language from a distant planet...

---

### Post by Mordorg on 2008-11-06
> **bscbrit said:**
> 
I'm not quite sure of the fault.  Are you saying that you have already installed Ubuntu but it will not boot at all, or that once you have passed the Grub menu the display fails?  What exactly do you see during the boot sequence?  Bios, Grub, splash screen, log on?

If my questions do not even make sense to you, let me know and I will rephrase them.  You might be new to Linux but understand computers very well, or the terminology might as well be a language from a distant planet...

I did install, but I had to set the installer to safe mode, and asci:off otherwise I got the same black screen when trying to install. The system boots, and grub comes up. But when I ask to load Ubuntu, or Ubuntu Recovery mode the screen will go black, and leave a flashing cursor at the top of the screen.

---

### Post by Mordorg on 2008-11-06
I played around with it some more, and seeing so many issues posted with ATI cards put in a OLD Geforce 4,and I got a little further. Now if I try recovery mode it will start loading, but it hangs and freezes on this line;

0.029728 ACPI : Checking Initramfs for Custom DSDT

---

### Post by WWSmith36 on 2008-11-06
I recommend to try some boot options that are used by the kernel

Here is a good page to check out for boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I think you might need acpi=off

---

### Post by mapes12 on 2008-11-06
Hi 

Would you let us have a look at at your setup please? Post the output to ```
sudo lshw
```

---

