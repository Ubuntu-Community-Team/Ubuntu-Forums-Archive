---
title: "usb 1-2: device not accepting address 2, error -71"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by farueulogy on 2008-04-26
Having install 8.04 everything is working fine *however* I noticed my start-up is a bit stuttery.

After turning of my splash screen I noticed this dialog hanging on:

"usb 1-2: device not accepting address 2, error -71"

I did a google search and mostly found information about "error -110" but nothing helpful.

Any idea what this means and if I can fix it to speed my start-up?

---

### Post by annda on 2008-04-26
i've had similar messages referring to my usb cd drive. and others complaining about the apple keyboard with usb hubs (mostly the hubs). but this is not limited to ubuntu, it's the kernel...

do you have external devices connected at boot?

---

### Post by farueulogy on 2008-04-26
I have a USB mouse. I also have 6 usb ports divided into one set of two and one set of four -all part of my laptop.

---

### Post by farueulogy on 2008-04-26
I rebooted with the mouse removed and the error did not appear and it seemed a bit quicker. However - I really need my mouse.

---

### Post by farueulogy on 2008-04-28
bump

---

### Post by Cypher on 2008-04-28
Is the mouse relatively new and a good brand?

A quick primer on USB:
USB devices need a unique address to communicate with your PC. By default when they are first "discovered" all devices use address 0. When the PC finds the device, it gets a new unused address from a pool of 255 possible addresses and hands it to the newly found device. This device should accept the new address and use that for further communication. So if you have a USB keyboard and USB mouse. Assuming the keyboard was found first, it would get address 1 and the mouse would get address 2.
-- End primer

Now does the mouse work after the delay?? If it does, it's possible that the PC tried a different address and that might have worked..

---

### Post by farueulogy on 2008-04-30
The mouse works fine - It's a dell optical basic mouse and on previous ubuntu versions not produced this problem as far as I'm aware. There has certainly been no start-up slow-down (Other than 7.10 which was the splash being stupid).

---

