---
title: "Has anyone installed 14.04.2 on a windows pre installed HP Pavilion15?"
date: 2015-07-27
forum: New to Ubuntu
---

### Post by kapi on 2015-07-27
Has anyone installed 14.04.2 on a windows pre installed HP Pavilion15?

The reason I ask is that I have installed the Ubuntu twice and am still getting a few niggly problems. 


[LIST]
[*]Keyboard settings are wonky, some keys don't work with shift+, 
[*]Keep having to reboot when things go wrong as above, 
[*]Password not recognized sometimes (may be because keyboard is off), 
[*]Netflix has flicker through center of screen, 
[*]Gimp keeps crashing.
[/LIST]


Wondered if it was something to do with the fact that I allowed 'legacy software' and disabled the UEFI in the system settings. (Don't think it is)

I've used Ubuntu for years as my main OS, installed it on numerous pc's and also have the 32bit version of 14.04.2 on an older laptop and all works fine

The HP Pavilion however seems to hate Ubuntu, could it be something I'm doing wrong as I've never had to disable the UEFI before? 

May just try the most recent version, maybe that'll help

Any feed back would be really appreciated

---

### Post by dino99 on 2015-07-27
better to go with 15.04; 14.04.x has plenty of nightmares and the fixes never come

---

### Post by oldfred on 2015-07-27
HP's are not UEFI friendly. They are one of several vendors that modify UEFI to also check description of UEFI entry to see if it says "Windows". That is not per UEFI spec.
So we have several work arounds depending on how you install to have it work in UEFI mode with Ubuntu only or dual boot.

Do not force reboot, remember the elephants.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Some systems have UEFI/BIOS settings to correctly enable keyboard. I think most are for USB ports. Not sure about your system.

May not apply to your system.
       
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by kapi on 2015-07-27
I've just handed the laptop back to pc world as the typing worked fine with a usb keyboard but with the built in one. 

Will try the most recent version of ubuntu as suggested when I get it back though if I still get problems. 
I'm back using ye old faithful for the time being (Toshiba satellite -L300) 

Thanks for the feedback

---

