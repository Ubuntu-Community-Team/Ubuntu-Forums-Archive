---
title: "Problems with commands to install driver"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by emma2 on 2013-08-11
Hey

I am trying to install my soundcard, and the instructions i have been given are:

The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.






Quick install


=============
In terminal,


1) Goto source directory
2) Execute make command as root
   make
   make install


Im a first time user and have no idea what this means in code, can anyone help?

Much appreciated!

---

### Post by Cheesemill on 2013-08-11
Which soundcard do you have and what version of Ubuntu are you using?

You may not even have to install drivers.

---

### Post by emma2 on 2013-08-11
I am running 12.04, i tried 13.04 but my system glitched out so tried 12.10 which had same results so back to 12.04.

its a Creative PCI Express X-Fi Titanium Fatal1ty Pro. My mobo is picking up the souncdard as I can see it available in the terminal but haven't managed to get any sound out yet. My cd/dvd drive also hasn't installed itself so until I find out how to install the drivers, similar to above, then I can't use the standard driver discs either.

---

### Post by SweetAurora on 2013-08-11
The PCIe versions of the X-Fi's have no linux support. **Drivers for them** **do not exist**. Only the older PCI versions of the X-Fi's are supported.

---

### Post by SweetAurora on 2013-08-11
Also the driver you are trying to use is from 2008 and is no longer usable in it's current state. Anyways, a couple of years ago Creative handed over the source and spec of the X-Fi PCI edition cards to ALSA. The driver is now included by default in linux as the ctxfi driver. Sorry for your lack of support on the card, Creative as a company just won't support Linux all that well.

---

### Post by emma2 on 2013-08-11
I found the drivers and have them though, I just need to know how to run them in the terminal? The card is being picked up aswell...

[http://support.creative.com/downloads/welcome.aspx?nDriverType=1#type_1](http://support.creative.com/downloads/welcome.aspx?nDriverType=1#type_1)

---

### Post by SweetAurora on 2013-08-11
You need to understand that driver **IS FROM 2008**. It's no longer supported in linux. That driver came out when we were still using Linux 2.6. We are now at Linux 3.11. It can no longer compile against the newer kernels. Instead, the updated version **BASED ON THAT DRIVER **is already included in the Kernel as **snd-ctxfi**. Your card just isn't supported by the driver. It can be detected, but not used. 

The last good Creative Labs sound card ever released that was 100% compatible with Linux was the Sound Blaster Audigy 2. The X-Fi's have horrible support. I personally use a Sound Blaster Live! Was using a X-Fi XtremeGamer (PCI) up till a few moments ago, but couldn't get all the features to work.

---

### Post by emma2 on 2013-08-11
So is there no way of me doing is manually through the terrminal?

---

### Post by SweetAurora on 2013-08-11
Sorry, but no. :(

---

