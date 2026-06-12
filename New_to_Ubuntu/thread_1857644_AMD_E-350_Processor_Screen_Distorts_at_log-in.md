---
title: "AMD E-350 Processor Screen Distorts at log-in"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by 2017 on 2011-10-10
I have a brand new HP model HP100 B all-in-one
AMD E-350 Processor 1.60 Hz
32 bit operating system
Windows 7 Professional 

I downloaded Ubuntu 11.04 32 bit (latest release)
I have program (Ubuntu)  on usb stick and running along side Windows 7 Professional.

during normal start into Ubuntu from hard drive screen becomes distorted after start up.
If I log into USB stick for start up I can get to into grub screen. 
I am total new to Ubuntu. I figure I have to load proper graphic card device drivers. I searched forum and am not exactly sure what to do next.

appreciate if I can get some help. New to command line as well.

---

### Post by 2017 on 2011-10-10
I can get into GNU GRUB version 1.99~rcl 13ubuntu3 minimal bash

---

### Post by shad0w_walker on 2011-10-10
I can't say with any certainty this will work, but I had an ATI card a little while ago which gave me some hassle.

If you can, in grub, add this to the end of the kernel options: 

```
nomodeset
```

Sometimes the kernel tries to be excessively fancy and it can cause serious headaches with certain cards. The line you want to put that on usually has stuff like 'splash quiet' and some other options on it.

---

### Post by 2017 on 2011-10-10
Thanks. That appears to have worked. Not sure if it's temporary fix or permanent. But thanks some much for help. I will be tooling around with this tonite

---

### Post by wildmanne39 on 2011-10-10
Hi, welcome to the forum! The nomodeset the way that you used it is only for one boot, hopefully there is a video card driver for your card in additional drivers, activate it and reboot then see if you can boot without issues, if not here is a link for nomodeset explaining it better.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

To install the driver you would have had to make the usb stick persistent, so you might want to wait until you install ubuntu to actually install the driver.
Thank you

---

### Post by 2017 on 2011-10-11
hey i downloaded the new drivers once i got into Ubuntu and now im fully up and running. Ubuntu is great. Thanks for help.

---

### Post by wildmanne39 on 2011-10-11
Hi, your welcome! that is great, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

