---
title: "I need to update the bios on a netbook that originally ran windows 7"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by dwalters14 on 2013-11-29
I need help. I have an Acer Aspire One d257 netbook that is not properly charging and has lost all wifi capabilities. Various forums have suggested that updating the bios would help, but the bios update is a .exe file, as this model was originally ran windows 7. How do I update the bios? Is there a way to confirm if these problems are indeed a result of a faulty bios? Also, if anyone knows what might be causing this problem, I am trying to boot Joli OS from a flashdrive to replace ubuntu. I have properly written the iso on another computer (tested it on another computer to confirm), and have prioritized usb flash drive in the bios boot order. However, when I boot the computer, I get nothing but a black screen with a flashing cursor in the top left corner. The computer then becomes totally nonresponsive and I have to turn it off by holding down the power button. I suspect this may be a bios related problem as well.

---

### Post by rburkartjo on 2013-11-29
does this link help
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by Frogs Hair on 2013-11-29
You may want to see the first link before getting too involved with Joli Cloud . The Joli drive is a good alternative and if you are looking for a cloud centered OS consider Peppermint,

[http://www.omgubuntu.co.uk/2013/11/jolicloud-desktop-to-be-discontinued-december-2013](http://www.omgubuntu.co.uk/2013/11/jolicloud-desktop-to-be-discontinued-december-2013)

[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by grahammechanical on 2013-11-29
Do you not have a user manual that explains how to update that BIOS? Perhaps the manufacturer's web has a PDF file that you can download? A BIOS exe file can sometimes be run from floppy disk or some other kind of external drive. Do not be too quick to update the BIOS.

I do not understand how failure to charge a battery could be a BIOS issue. More likely a failing battery problem. Or a failing charger problem. I guess that when the power gets very low the machine may disable the WiFi adapter to preserve battery power so that you do not suddenly power down and lose data.

When trying to install Joli OS do you really get absolutely nothing? Or do you get something and then after a while the flashing cursor appears. That something might be a clue. It could be that you may need to run the installer of Joli OS using the nomodeset option. We sometimes have to do this with the Ubuntu installer.

Regards.

---

### Post by Mark Phelps on 2013-11-29
> Various forums have suggested that updating the bios would help, 

BEFORE you do any BIOS update, you need to ensure that BOTH of the following are true:
1) You have a way to save off the current working BIOS to a medium that can be used to restore it -- without having to boot into an OS
2) You have a way to boot into an app that will allow you to restore the BIOS from the saved version

BIOS updates are NOT the miracle cure that everyone seems to believe!  Unless you know for sure that the BIOS update fixes the problems, you are really better off leaving the BIOS alone.  A failed BIOS update without BOTH of the above being true will turn your PC into an "electric brick".

---

