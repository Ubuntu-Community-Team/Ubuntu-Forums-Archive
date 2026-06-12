---
title: "new guy - questions"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by A-Jay on 2012-01-03
I have a 8+ year old HP 764n  Pent 4 2.66 GHZ  that was just loaded with 10.04 is there any good reason to change this to a newer version, Will my classic computer run the newest version. I am new user, don't do anything fancy basic web, you tube, music (ipod) and shop cars and parts. I have not been able to get my od printer to work, have checked for a driver have not found one.  I have 3 questions.
1. Should I get a newer version
2 Would a wireless printer/all in one be better otr stick with a USB 
3. I need advise for a wireless card internal slot type or a USB type Any suggestions on type or model. I just upgraded to FIOS 

Thanks for your answers/advise   A-Jay

---

### Post by Bucky Ball on 2012-01-03
If it's not broke don't fix it! 10.04 LTS is the current long-term support release (supported until April 2013) and if it's working for ya I'd stick with it.

If you have room you could install a newer version on another partition to tweak, experiment and play around with, and keep the stable 10.04 LTS right where it is. ;)

I have a Brother wireless printer and it works a treat ... This printer has the option of ethernet cable, USB or wireless ... whichever you fancy using.

---

### Post by QIII on 2012-01-03
1.  Not if 10.04 is working for you now.

2.  Wireless can be frustrating because of lack of OEM driver support for Linux.

3.  Atheros has good wireless support.

---

### Post by elytron on 2012-01-03
Hey, checkout the **D-Link DWA-552** PCI wireless card.

---

### Post by A-Jay on 2012-01-04
Thanks for the info, I will stick with the 10.04 seems fine. I hooked up a different printer (HPc4280) seems to be printing ,have not tried the scanner yet, not where the info goes after I scan.  

About the D-Link 522 where do you get a driver, I checked documentation on WEB but did not see any Lunix support ? Would my computer be slower using wireless or would the card still be faster than the computer anyway. I had 1.05 mbps on DSL, now have 20.72 mbps with FIOS.  Thanks again !

---

### Post by Chiel92 on 2012-01-04
Would you give your threads titles making sense?
This way people do not know what the thread is about.

---

### Post by sanderd17 on 2012-01-04
> **A-Jay said:**
> Thanks for the info, I will stick with the 10.04 seems fine. I hooked up a different printer (HPc4280) seems to be printing ,have not tried the scanner yet, not where the info goes after I scan.  

About the D-Link 522 where do you get a driver, I checked documentation on WEB but did not see any Lunix support ? Would my computer be slower using wireless or would the card still be faster than the computer anyway. I had 1.05 mbps on DSL, now have 20.72 mbps with FIOS.  Thanks again !

Most of the time, drivers for wireless cards are compiled directly into the kernel (so you don't need to install them). The only exception I know are broadcom cards.

For the scanner, Sane is a backend with drivers for most scanners: [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

To do real scanning, you need a tool like Xsane, skanlite of simple-scan.

For the printer, you need to look at a bit of CUPS documentation.

---

### Post by I_can_see_the_light on 2012-01-04
> **Chiel92 said:**
> Would you give your threads titles making sense?
This way people do not know what the thread is about.

To be honest I think the thread title is perfectly in order. We can't expect every new user to know how to name their first threads the best way. As it is, I think that we get all the info needed - a new guy with a couple of basic questions.

---

### Post by Ms. Daisy on 2012-01-04
To echo & add weight to what others said, don't fix it if it ain't broke. 10.04 is the long term support release. No reason to change unless you love to tinker.

---

