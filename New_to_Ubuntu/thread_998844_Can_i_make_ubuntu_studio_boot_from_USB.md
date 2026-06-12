---
title: "Can i make ubuntu studio boot from USB?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by sharks on 2008-12-01
I installed II and saw Create a bootable USB option... Can i use it to make other OS such as Ubuntu studio , Mandriva , etc... to boot from USB?

---

### Post by fr.theo on 2008-12-01
you should be able to so long as you set your usb to be the primary boot disk in your bios or if you have a bios with an F8 etc.. function setting that allows you to select you boot device without entering the bios then yes it should, so long as you have a USB stick that is bid enough or a usb Drive.

---

### Post by gunashekar on 2008-12-01
I tried using "Create a bootable USB" option to install Linux mint and it did not work.

---

### Post by snowpine on 2008-12-01
> **sharks said:**
> I installed II and saw Create a bootable USB option... Can i use it to make other OS such as Ubuntu studio , Mandriva , etc... to boot from USB?

Hi Sharks, Ubuntu Studio does not have a live CD, as far as I know, so I don't think you can use the Intrepid USB creator.

However, you should be able to *install* Ubuntu Studio to a large enough USB device (probably would need 8gb). Just use the regular installer, then when you get to the final step, click the Advanced button and make sure you install the bootloader to the USB stick, not your internal hard drive. I have used this method with several different distros so I think it *should* work with Ubuntu Studio--please let me know how it goes. :)

---

