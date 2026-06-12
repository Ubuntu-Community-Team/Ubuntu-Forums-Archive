---
title: "USB not in my BIOS"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by rickyLOLZ on 2012-01-28
So i wanted to install Ubuntu 11.10 with my USB, but i don't want to waste more money on DVDs, they don't work.

But my bios doesn't let me boot from USB...
[IMG]http://i39.tinypic.com/2ywbxjc.png[/IMG]
Even if i try to boot to the bios and do the same thing the thing to select USB won't appear.

Please help,
Ricardo.

---

### Post by BC59 on 2012-01-28
Look here:
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by Double.J on 2012-01-28
+1 to plop :)

It may also be worth seeing if your manufacturer has released a BIOS update that addresses this - many have, and some (such as my netbook) even added options to the BIOS for running non windows systems :D

To install a BIOS update, you would normally either need an existing windows/dos install, or it can be done from freedos... though you'ds need plop to boot the live stick... which may defeat the point, but may still be worth it if there's some good things from the update?

All the best :)

---

### Post by Rex Bouwense on 2012-01-28
In some machines the USB flash drive is recognized as another hard drive.  You can check that and insure the flash drive is first and the hard drive is second.

---

### Post by grahammechanical on 2012-01-28
With my desktop motherboard I had to disable the legacy floppy drive option and then I got a complete section on USB in the BIOS which allowed my to set speeds and also put USB in the list in the boot section.

Regards.

---

### Post by Miljet on 2012-01-28
On my Toshiba laptop there is no USB option in the BIOS unless there is a USB drive actually plugged in. I thought for a long time that it didn't support booting from USB. Then one day just for grins, I plugged in a USB stick and booted into the BIOS and the option was there to boot from USB.

---

### Post by fantab on 2012-01-28
In some Mother Board BIOS the USB booting is disabled by default and so is PXE Boot. You may have to manually enable it.

---

### Post by halitech on 2012-01-28
what type of machine do you have? it's possible that the machine just doesn't support it

---

