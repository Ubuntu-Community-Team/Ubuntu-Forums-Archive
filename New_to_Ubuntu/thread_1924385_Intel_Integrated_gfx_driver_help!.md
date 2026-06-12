---
title: "Intel Integrated gfx driver help!"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by Elleryia on 2012-02-12
Hello all, 
 I'm trying to get the integrated Intel graphics in a box I put together. Onboard wireless works fine as do all the other basic drivers. Its only the display driver that is giving me trouble. The motherboards website is:
 [http://206.108.48.60/app/en/mb/introduction.php?S_ID=518&tab=3](http://206.108.48.60/app/en/mb/introduction.php?S_ID=518&tab=3). 
Biostar says its integrated Intel Graphics Media Accelerator X4500. ( Intel® X4500). 

System specs
Intel Core 2 duo e8500 3.16 Ghz
4 GB Mushkin DDE3 1333 Mhz Ram
Biostar G41D3C Motherboard
  Things Ive tried. 

I tried to update the driver and use a fix I found in the forums. Im using 11.04. 
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty[FONT=Verdana]
[/FONT]sudo add-apt-repository ppa:glasen/intel-driver  sudo apt-get update && sudo apt-get upgrade

This is successful so I make the /etc/X11/xorg.conf file to support the intel driver. 
ection "Device"         Identifier      "Configured Video Device"         Driver          "intel" EndSection  Section "Monitor"         Identifier      "Configured Monitor" EndSection  Section "Screen"         Identifier      "Default Screen"         Monitor         "Configured Monitor"         Device          "Configured Video Device" EndSection
The I reboot, get back into ubuntu and nothing is different. System still says unknown display. I have also tried using vesa in the xorg.conf file. This created some booting issues that appear to have been resolved by:
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf sudo update-initramfs -u

But again the system does not detect the display and I cannot adjust the 
resolution. 

Does anyone have a way to get this integrated gfx chip working?
Or does anyone have a recommendation on a cheap gfx card that is 
known to work well in 11.04 or 11.10?

---

### Post by Elleryia on 2012-02-12
The contents of the xorg.conf file. 

Section "Device"         
Identifier      "Configured Video Device"         
Driver          "intel"  
EndSection 
 Section "Monitor" 
        Identifier      "Configured Monitor"
EndSection  
Section "Screen" 
        Identifier      "Default Screen" 
        Monitor         "Configured Monitor" 
        Device          "Configured Video Device" 
EndSection

---

### Post by MikeDK on 2012-07-21
Here's mine from my X4500HD integrated graphics

> Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver      "intel"

# For better OpenGL performance
	Option      "FramebufferCompression" "True"
EndSection

Section "DRI"
    Mode 0666
EndSection

IF you need better openGL performance just change the FrambufferCompression to "false" instead of "true".

You could backup your xorg.conf as xorg.conf_backup and replace it with this one, it SHOULD work with any x4500 chip from the G45 chipset

Hoe this helps you.
Kind regards mikedk

---

