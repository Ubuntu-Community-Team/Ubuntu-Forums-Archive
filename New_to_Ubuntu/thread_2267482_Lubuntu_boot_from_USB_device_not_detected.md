---
title: "Lubuntu boot from USB device not detected"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by ben144 on 2015-03-01
I just recently downloaded the Lubuntu Iso file to my USB and tried to boot it from bios and I got an error that said PXE-E61: Media Test failure, check cable.

I tried to use other USB slots but the same result. Any ideas as to how this can be fixed?

-Ben

---

### Post by Bucky Ball on 2015-03-01
Welcome. Did you drag and drop the ISO file to the USB? If so, that won't work. If you're using Windows you need to use something like [Universal USB Installer ]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")to create a bootable USB, restart, change the boot device in BIOS (on lots of machines you can hit F12 at boot and that will take you to a boot device options screen) to the USB.

---

### Post by gordintoronto on 2015-03-02
You selected the wrong option in your BIOS. PXE is essentially "boot from my Ethernet port."

---

