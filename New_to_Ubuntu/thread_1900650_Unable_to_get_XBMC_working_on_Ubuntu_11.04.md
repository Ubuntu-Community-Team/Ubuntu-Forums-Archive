---
title: "Unable to get XBMC working on Ubuntu 11.04"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by jhazard112 on 2011-12-26
Hi all,

I am having issues getting XBMC to work on Ubuntu 11.04.  I have an Acer Aspire 7741-4433, and I have installed XBMC, but when I try and run it I get the following error:

"XBMC needs hardware accelerated OpenGL rendering.  Install an appropriate graphics driver."

I am not sure what I should do, so I go to the command line and throw in the following command:

lspci

To see what video card I have and I am running, and this is the output that I get:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

So I am not sure what type of video card this is, how I can get a driver for it, or how I can get OpenGL rendering for this card, but if anyone can assist I would greatly appreciate it.  Thank you all in advance.

---

### Post by Gone fishing on 2011-12-27
Sounds like you need to install the appropriate driver, open the dash and search for additional drivers. Do you have a driver you can install ifso install it.

If there is no driver listed open a terminal and run sudo apt-get update and try again. If there is still no driver listed what hardware are you using?

---

### Post by jhazard112 on 2011-12-27
I have tried all of this, and it still does not work.  I am running an Acer Aspire 7741-4433.  All the information that I have listed, should be the hardware that I am running.  Is there something else that I could try to see exactly what I am running for my video?

---

### Post by Gone fishing on 2011-12-27
Is this and [http://ubuntuforums.org/showthread.php?t=1229345&highlight=Intel+GMA+HD](http://ubuntuforums.org/showthread.php?t=1229345&highlight=Intel+GMA+HD) this relevant [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

If not give a little more detail on the video card sudo lshw

---

### Post by jhazard112 on 2012-01-04
Sorry I haven't gotten back to anyone that has been helping, but here is what has happened.  I tried to install the GMA 500 driver, and my screen went blank on reboot.  Tried to recover and remove, and nothing was working.  So I tried something a little weird.  I reverted to Ubuntu 10.04 64-bit and installed XBMC, found it worked with no problems.  I am not sure what is going on with this, but it has certainly gotten interesting...anyone with any information please help.

Hazard

---

