---
title: "Problems installing 11.04"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Scard on 2011-10-04
I recently tried to install 11.04 (64bit)from a flash drive.

It boots up and starts the installation normally, and after I select the option to install to Hard Disk, the screen goes black. (and I can barely make out the outline of the installation menu. with the language options and whatnot...)

I downloaded the ISO and USB Installer a few more times, but that that wasn't the problem. The flash drive is brand new.

I would appreciate any help.

---

### Post by meatytaco on 2011-10-05
Probably not the case, but have you tried installing a different distro just to see if it actually works?

---

### Post by mastablasta on 2011-10-05
it could simply be that graphics card is not supported during install (though that's a bit strange). what you could do is use alternate install and then try using various boot paramters such as using nomodeset.
 
btw can you boot into live session? if not then try one of the boot parameters. i would first try nomodeset.

---

### Post by Scard on 2011-10-05
After trying 11.04, I tried 10.04 using the same method and it worked just fine.

during the install for 11.04, it looks as if the backlight to my screen is off.

---

### Post by amjjawad on 2011-10-05
> **Scard said:**
> I recently tried to install 11.04 (64bit)from a flash drive.

It boots up and starts the installation normally, and after I select the option to install to Hard Disk, the screen goes black. (and I can barely make out the outline of the installation menu. with the language options and whatnot...)

I downloaded the ISO and USB Installer a few more times, but that that wasn't the problem. The flash drive is brand new.

I would appreciate any help.

Hello and Welcome :)

First of all, you need to check MD5SUM and make sure to use the right tool to create your LiveUSB.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I prefer UNetbootin but that's me.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Once you make sure step 1 and 2 are done successfully, we can check other stuff.

---

### Post by wildmanne39 on 2011-10-06
Hi, here is a link to help you set parameters as mastablasta mentioned.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

