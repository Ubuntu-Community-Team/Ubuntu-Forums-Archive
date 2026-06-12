---
title: "Running live cd does not mean a lap top will work once ubuntu is installed"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by paulravin on 2014-05-29
My recent experiance against commonly promoted ideas has been that running a live cd on the computer in the shop before purchase does not mean that computer will work on that machine after install. 

You are taking on a complete gamble. I am 2 brand new computers into just getting Ubuntu to work, should I buy a third?

To be sure I would say each component of hardware has to be checked off as multipul ubuntu users confirming it will work.

---

### Post by QIII on 2014-05-29
Hello!  Can you give us the hardware specifications?  What was the behavior you observed?

Two of the most common causes of this are hybrid graphics or the need to to use the nomodeset option on first boot to get to the desktop and install the proprietary driver or make the nomodeset option permanent.

These can be dealt with without assuming that the general conclusion is that a Live session is not a valid test.

---

### Post by mastablasta on 2014-05-30
still it's not a valid test. when i test live CD my sound card gets propperly recognised. digital surround sound is on. upon install it defaults to dummy output. then you tell it to use digital surround. it works for a while on a third or so reboot (not sure what this depends on) it again goes to dummy only this time digital surround dissapears. ok i switch to digital stereo and again it works for some time an the whole thing is repeated. until i land with analog stereo. which when it defaults to dummy output i have quite a bit of trouble getting it back. 

anyway point is it all works quite well on live CD...

---

### Post by monkeybrain20122 on 2014-05-30
I don't test with a live usb. I have a full install of Ubuntu in an external hard drive, which is a clone of my 'real' system except for some hardware specific tweakings and user data. I use it as a portable and also to test new hardware. If that works it guarantees that a real install would work (just clone it over. :))

---

### Post by sudodus on 2014-05-30
That's a good test, monkeybrain. Maybe rather tough, but good :-)

I can do the same with my 'installed system' in a USB pendrive.

---

### Post by paulravin on 2014-05-30
I have solved it!!!  
 

 Or credit where credit is due, the guys at Acer out of scope technical support (From Australia 1800 144 519) worked out why my screen would not work.  
 

 From my understanding it is windows again, trying to re invent everything. When I originally installed 14.04 I did not change anything in bios so it installed under the boot mode UEFI.
 

 I have re installed 14.04, first I went to:
 

 F2 Bios
 Boot
 Boot mode
 Change from UEFI to Legacy
 Choos USB as first boot option
 F10 save and exit
 Install Ubuntu.
 

 Everything on this Acer V7 now works. Maybe it is fair to say that when running from a live CD it is a good indication that every component that works with live CD can work once ubuntu is installed. The can work bit took me 1 week of half days, communication with _5 different tech support / linux savy people_, lots of trawling the web, posting messages etc.  
 

 Fixed now, just so releaved to not have to go back to the continual headache that is windows. Thank you Acer tech support, they charge $75 and it was worth every cent. When trying to fix a HP I also found the best and fastest way to solve problems was HP tech support threats of warranty voiding bla bla but they fixed my computer issues where no one else could.

---

