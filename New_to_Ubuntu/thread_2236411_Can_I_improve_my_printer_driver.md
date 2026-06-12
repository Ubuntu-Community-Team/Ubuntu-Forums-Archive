---
title: "Can I improve my printer driver?"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by LizzyJean on 2014-07-26
I started using Ubuntu in April on my Dell laptop.  I use my printer  - Canon PIXMA MX860 Ink Jet - a lot for my music teaching business and have some issues:

1. It freezes up after most jobs and I have to unplug it (awkward) to reset it.  (This mostly happens when I print from LibreOffice, but sometimes happens from Firefox or Document Viewer).
2. Everytime I reset it, it does a self cleaning so I'm going through ink, like, seriously, 10 times as fast.

Any suggestions?

---

### Post by whitesmith on 2014-07-26
You won't like this, but I also bought a Canon printer because it was on sale. I could never get it to work with drivers in CUPS, and wound up giving it to my wife to use with That Other Operating System. I bought an HP M1212mf, which worked out-of-the-box with both 12.04 and 14.04, although I can't attest to the faxing capability since I have no need for that technology. My advice is to retire the Canon and go with an HP. At least that company recognizes the FOSS community and works with us, whereas we are seemingly invisible to Canon. Cheers.

---

### Post by LizzyJean on 2014-07-27
You're right, whitesmith:  I don't like it.  But I appreciate the benefit of your experience.  My last printer was an hp and I hated how controlling it was about changing the ink.  (I can usually get a lot more ink out of a cartridge than the printer thinks I can.) But it's good to know that hp is willing to work with the FOSS community. I will start reviewing hp printers and see if I can find one that's more hassle free.

But I'm also still holding out to see if anyone has Canon advice. :)

---

### Post by pdc on 2014-07-28
Hi Lizzy; 

I wonder if you installed the (linux) drivers that Canon supplies: it may well be that you have gutenprint installed; a very good open source driver that covers many printers:

here is a link for the debian package that Canon supply for the MX860 device;

this device is 5yrs old; and then 32bit drivers were released; one can install the 32bit drivers; (if one has installed a 64bit ubuntu); and make what are called symbolic links: where one tells the system to look in lib instead of lib64; where it thinks things should be ..............

Ubuntu has dropped libtiff4 so one would install that too; it can be hard to blend "cutting-edge" with stability..................................

---

### Post by coldraven on 2014-07-29
Before you buy any printer do an online search for <printer model> CISS
CISS stands for Continuous Ink Supply System. There are two kinds, one has external tanks of ink the other uses re-fillable cartridges.
I have an old Epson R300 six colour printer. I used the external tank system for several years without any problems and I could fill the tanks easily with a funnel!
The only drawback is that it is difficult to move the printer to a different location.
Now I'm using the re-fillable cartridges and have to use a syringe to put the ink in. They have auto resetting chips to fool the printer into thinking that they are new each time :)
Either way, my ink now costs about £10 per litre. If you buy from Cannon it will cost about £1000 per litre!!
With six colours I get good photo prints and it's the paper that costs the most.

Edit: I bought both versions from Ebay and they are not expensive.

---

