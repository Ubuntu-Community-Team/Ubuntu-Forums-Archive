---
title: "Ubuntu 13.10 won't boot following install"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by wade5 on 2014-02-09
I have just purchased a new desktop pc and am hoping to run ubuntu on it.  There is no other operating system currently installed on the system.  I have created a live cd for ubuntu 13.10 and begun the install.  It reached near the end when i recieved an error message that grub2 could not be installed.  i tried several times using multiple disks.  eventually i downloaded boot repair disk, burnt it to a cd and ran that in my pc.  It said boot repair was successful and i can now reboot.  I am now able to get into the Grub2 boot menu and select Ubuntu.  However i am unable to get past the ubuntu splash screen where the loading icon appears.  I left it for a couple of hours and it is still stuck on this screen.  Could someone please send me in the right direction as this is my first time dealing with a linux distro and i'm feeling rather overwhelmed.  I'm not sure what info i need to supply to fix this problem so please let me know.  Thanks

[http://paste.ubuntu.com/6901818/](http://paste.ubuntu.com/6901818/)

---

### Post by oldfred on 2014-02-09
If you get grub menu you are past what Boot-Repair can usually fix.

What computer is this and what video? 
Often issues of black screen or related not booting then need boot parameters to get video to work and it depends on which card/chip you have. And sometimes other parameters are needed instead or also.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    You also have this issue on sda?
Invalid MBR Signature found.

Is it not partitioned/formatted?
Is sdb a SSD?

---

### Post by wade5 on 2014-02-09
thanks for the reply

Intel Core i7 3770K/ 3.50GHz/8MB cache/LGA1155 Ivy Bridge
Asrock Z77-PRO3 Z77/4 x DDR#/1 x PCI-E3.0/2 x SATA/4x USB3.0/ HDMI/D-
Team 8GB single DDR3 1600MHz c9 elite
LG H24NSB0 SATA 24X+- supermulti DVDR Black OEM

sda= Seagate SATA3 1TB 7200 RPM 64mb cache
sdb= Kingston 120GB HyperX SSD SATA3

There is no video card installed

As far as i know, the ssd was wiped and partitioned during the install. is there a way to see if this was done succesfully?
I havent tried installing on sda, should i give that a go? 

I tried modifying the grub entry with "nomodeset" and "libata.force=noncq" to no success

Is there anything else i should have done up to this point, besides unboxing of the pc and installation of ubuntu from the CD?

Regards

---

### Post by oldfred on 2014-02-09
The nomodeset works for nVidia, but Intel often needs other settings.

Some of these were more for laptops. If specifing size you must use your default or standard monitor size  not examples 1280x1024 shown.

 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

 Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)

---

