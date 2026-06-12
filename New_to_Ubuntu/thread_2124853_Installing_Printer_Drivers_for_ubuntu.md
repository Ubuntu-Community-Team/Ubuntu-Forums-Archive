---
title: "Installing Printer Drivers for ubuntu"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by cadnomad on 2013-03-12
Hi all, I've just started using ubuntu 12.10 and run cad software on it such as draftsight. 

I need to take out prints from time to time but Hp (Designjet 110 plus) and Canon (iR 2318L) do not seem to have a printer driver for ubuntu.

Is there a way to get around this by installing Wine and windows drivers? (I guess it's a shot in the dark) or any other way where I could use said printers to print from my ubuntu system?

---

### Post by Cheesemill on 2013-03-12
I think you're out of luck, it appears that neither of these printers have any Linux support at all.

[http://hplipopensource.com/hplip-web/models/designjet/hp_designjet_110.html](http://hplipopensource.com/hplip-web/models/designjet/hp_designjet_110.html)
[http://software.canon-europe.com/products/0010737.asp](http://software.canon-europe.com/products/0010737.asp)

Wine isn't an option as is doesn't work with drivers, only applications.

---

### Post by pdc on 2013-03-12
actually by checking the Canon Asia website, I think this device is supported by the ubiquituous Canon UFR driver; 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

It comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

If only you had a 32bit system, life would be much easier; Canon provide .deb packages; and rpm packages; and 32bit drivers and 64 bit drivers; but for the latter, they only supply rpm packages ..........

for the 64bit, UFR driver install on ubuntu, there are several threads but this one seems to cover things

[http://ubuntuforums.org/showthread.php?t=2021854&p=12541322#post12541322](http://ubuntuforums.org/showthread.php?t=2021854&p=12541322#post12541322)

There seem to be 2 steps:
1) create several symbolic links 
2) convert rpm to deb and install them 

You need symbolic links; so it seems to work best to create those first

post #6 suggests

> [COLOR="#FF0000"]sudo ln -s /usr/lib64/cups/backend/cnusb /usr/lib/cups/backend/cnusb[/COLOR]

and 

> [COLOR="#FF0000"]sudo ln -s /usr/lib64/cups/filter/pstoufr2cpca /usr/lib/cups/filter/pstoufr2cpca[/COLOR]

and then the two more usual links

> [COLOR="#FF0000"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and > [COLOR="#FF0000"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]
_____________________________________________________________________________________________

......so that would be step 1: setting up symbolic links so things can be found...............rather like wives finding socks for guys, the symbolic links tells the computer where to go look!

........ then to the driver install..........................................

in post #1, che bizarro describes how he converts files with alien

in contrast, this thread

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

which seems to carry the imprimatur of Debian adminstration...........

says you can firstly convert and then install the converted files with the command

> [COLOR="#FF0000"]*sudo alien -i package-name.rpm*[/COLOR]

......one needs to ensure alien is already installed!!

> [COLOR="#FF0000"]sudo apt-get install alien[/COLOR]

as with all Canon packages ......install the **COMMON** ([COLOR="#0000FF"]cndrvcups-common[/COLOR])first, and then the **SPECIFI**C ([COLOR="#0000FF"]cndrvcups-ufr2-uk[/COLOR])

let us know how it goes and what can be clarified for you

____________________________________________________________________

If it would help you, I am happy to post the commands for the terminal to do the driver install; 

________________________________________________________________________

for the HP

[http://hplipopensource.com/hplip-web/install/manual/hp_setup.html](http://hplipopensource.com/hplip-web/install/manual/hp_setup.html)

this thread should get you going

> [COLOR="#FF0000"]sudo hp-setup[/COLOR] seems to be the magic command to open Aladdin's cave

---

