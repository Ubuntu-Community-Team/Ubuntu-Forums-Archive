---
title: "[SOLVED] Wireless Travel Mouse Drivers"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by dconstruct on 2008-05-23
I just bought a wireless travel mouse from Brookstone, this travel supply store in the mall and it just comes with a mouse and a USB thumb drive that plugs in to the laptop.  Being an idiot, I forgot to think about driver support with Ubuntu Hardy.  It didn't come with any installation CDs or anything, so I'm assuming the necessary drivers SHOULD be auto-accessible by the thumb drive, but when I plug it in, and go to Hardware Drivers, nothing shows up.  So, I searched the internet and couldn't find anything, but I didn't know if you guys and gals knew where I could search for the appropriate drivers or a could that I could use that would allow ubuntu to recognize the thumb drive for the mouse.

Thanks!

---

### Post by stchman on 2008-05-23
> **dconstruct said:**
> I just bought a wireless travel mouse from Brookstone, this travel supply store in the mall and it just comes with a mouse and a USB thumb drive that plugs in to the laptop.  Being an idiot, I forgot to think about driver support with Ubuntu Hardy.  It didn't come with any installation CDs or anything, so I'm assuming the necessary drivers SHOULD be auto-accessible by the thumb drive, but when I plug it in, and go to Hardware Drivers, nothing shows up.  So, I searched the internet and couldn't find anything, but I didn't know if you guys and gals knew where I could search for the appropriate drivers or a could that I could use that would allow ubuntu to recognize the thumb drive for the mouse.

Thanks!

What model is the mouse?  Give us an lsusb output here.  USB wireless devices like a mouse should work fine.

---

### Post by dconstruct on 2008-05-23
Bus 001 Device 002: ID 062a:0000 Creative Labs Optical Mouse

That's the lsusb output.  Creative Labs.  And, the brand is just Brookstone.  So, yeah, any help is appreciated.

---

### Post by dconstruct on 2008-05-24
Any ideas?  I have a trip in a few days and I need to be able to use that mouse, because my touchpad is going bad on me I think and I'd hate to have to buy a different mouse.

---

### Post by niteshifter on 2008-05-24
Hi,

It should work "as is", no special driver needed. The usbhid (installed by default) module should handle it.

BTW, that's not a thumb drive, it's the transceiver for communicating with the mouse. I also have a Creative Labs Optical Mouse, ID of 062A. Nothing happens with mine until press the button on the transceiver (it should start blinking slowly), then press the button on the underside of the mouse, then the transceiver blinks rapidly. Then the mouse works.

---

### Post by dconstruct on 2008-05-25
well now i feel like a fool.  ;)

it works.  i just didn't know i had to press the button on the receiver first before pressing the button on the mouse.  but now it works.  so, thanks a million.

---

### Post by wolterh on 2009-01-25
Well, this thread help me to make my mouse work. I thought it was both Wireless and 'Wiremore' mouse, but now I find out that it requires not only the usb cable, but the wireless usb to be plugged in.

Am I doing something wrong, or what's up with this mouse that can't just work with just the cable, like any other mouse?

---

