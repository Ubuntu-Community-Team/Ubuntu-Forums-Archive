---
title: "Problem trying to boot from USB"
date: 2018-08-04
forum: New to Ubuntu
---

### Post by etolocka on 2018-08-04
Hello
I would like to test how Ubuntu works on my laptop and for that, prepare a pendrive with Ubuntu 18.04 and Rufus, following the instructions. The problem is that I can not get the laptop to boot from USB. It has AMI BIOS 5.011 UEFI 2.4 and among the boot options the USB does not appear. I can not find any legacy or CSM mode.


If someone can help me, I will be grateful


Regards,
Ernesto.

---

### Post by oldfred on 2018-08-04
Is that newest BIOS/UEFI for your system?
What brand/model system? 

Many UEFI call UEFI Secure Boot as "Windows" or "Other", but mention if using Windows 7 use Other as 7 does not support UEFI Secure Boot.
And then even if Secure Boot off, you may have separate settings to allow USB boot or full access to USB.

---

### Post by etolocka on 2018-08-04
It is a Cloudbook running Windows 10, with 32 GB SSD and 2GB RAM

[IMG]https://ibb.co/iQcNDz[/IMG][IMG]https://ibb.co/nBhB6K[/IMG][IMG]https://ibb.co/gE0sDz[/IMG][[IMG]https://thumb.ibb.co/nBhB6K/IMG_20180804_190901368.jpg[/IMG]]("https://ibb.co/nBhB6K")

[[img]https://thumb.ibb.co/iQcNDz/IMG_20180804_190844860.jpg[/img]](https://ibb.co/iQcNDz)

[[img]https://thumb.ibb.co/gE0sDz/IMG_20180804_191417328.jpg[/img]](https://ibb.co/gE0sDz)

---

### Post by oldfred on 2018-08-04
Which model cloudbook?
With 2GB of RAM, on of the lighter weight Ubuntu flavors may be better.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors) 
    
Have you updated UEFI from Acer?

If installing internally you have to set "trust", but that should not be required to boot installer.
       Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by etolocka on 2018-08-04
It is not an Acer cloudbook. It is a "CX" brand, produced in Argentina. Probably from another origin assembled here with that brand.
I do not know what you mean by the "trust" option, the only boot options are those seen in the images attached in the previous post


Regards,
Ernesto.

---

### Post by oldfred on 2018-08-04
What is under Advanced settings, anything related to USB ports?

Also some systems work with one USB port but not another.

Are you sure USB flash is correct. Sometimes one installer like Rufus works, and then with some systems a different one works.
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[URL="https://help.ubuntu.com/community/Installation"]https://help.ubuntu.com/community/Installation

      [/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    

And sometimes one flash drive works and another does not.
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208) 

[URL="https://help.ubuntu.com/community/Installation"]
[/URL]

---

### Post by oldrocker99 on 2018-08-04
Make sure you boot in "Legacy" (or whatever the non-UEFI boot is), otherwise, from my experience, booting to an installation in UEFI mode will prevent grub from installing, making the computer unbootable.

And you don't want THAT.

---

### Post by Geoffrey_Arndt on 2018-08-05
Also . . . look for an option in the BIOS to add a "Supervisor" or "Administrator" password.   If the BIOS provides that, then reboot after setting the password and you will see some additional options for things like "Legacy" or CSM mode.

---

