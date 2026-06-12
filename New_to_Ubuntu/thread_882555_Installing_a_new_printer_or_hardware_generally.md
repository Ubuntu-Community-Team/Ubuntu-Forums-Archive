---
title: "Installing a new printer or hardware generally"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by jerryduk on 2008-08-07
Well I am delighted to have my new ubuntu system up and running. It even runs my Belkin USB wireless adpter without any extra drivers.

I now want to switch my HP 1100A printer from my old laptop to my new Ubuntu machine. I am sure there will be a guide somewhere to adding a new printer but I can't find it. Sadly I don't expect to get the scanning functions working but hope to get it printing at the very least.

[COLOR="Red"]Fixed - Installed printer as suggested by forest pixie then looked over the web for the scanner. Found something on Sourceforge - "HPLIP is an HP developed solution for printing, scanning, and faxing with HP inkjet and laser based printers in Linux" which enabled me to download and install software which works a dream and links to XSANE as suggested by Bucky Ball - Fixed my printer scanner in two hours on ubuntu. I spent last night trying to do the same on XP SP3 and gave up because it is unsupported

Bravo UBUNTU.[/COLOR]

---

### Post by Elfy on 2008-08-07
You should just be able to plug the printer in and use it - not sure about scan though.

Check it out on 

[www.ubuntuhcl.org](www.ubuntuhcl.org) - I tried but it appears to be down at the moment.

The rprinter was working ok with dapper so it should be ok still.

If you do have problems you can get the printer driver form here
[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

---

### Post by Bucky Ball on 2008-08-07
For scanning try the Xsane package. Look it up in Applications->Add/Remove. My (old) scanner was identified and usable immediately, to my complete and utter surprise I might add! :)

---

### Post by jerryduk on 2008-08-07
Thanks for the replies. The printer is a parallel port printer (not USB) and Ubuntu doesn't appear to see it or the scanner part of it. I reckon I'll have to install some drivers but not sure where to start.

---

### Post by Elfy on 2008-08-07
You've got it plugged in and turned on and it hasn't recognised it - have you gone to system - admin - printers and then tried to add printer - HP1100 is there as a choice.

Take no notice of the HP910 on the right I hadn't clicked on the 1100 when I took scrnshot.

IF not the link I gave above should help.

---

### Post by Bucky Ball on 2008-08-07
> **jerryduk said:**
> Thanks for the replies. The printer is a parallel port printer (not USB) and Ubuntu doesn't appear to see it or the scanner part of it. I reckon I'll have to install some drivers but not sure where to start.

JerryDuk: Did you read my last post and have you installed Xsane from Applications->Add/Remove??? It should get your scanner up pronto.

---

### Post by jerryduk on 2008-08-07
Many thanks - that's got the printer side working now I am looking for help on the scanner. Currently investigating sourceforge.

---

### Post by jerryduk on 2008-08-07
Thanks I looked at XSANE but it doesn't see the scanner. I reckon I'll have to try and find a scanner driver and install that before XSANE can see it.

---

### Post by colintivy on 2008-08-07
Hi folks

This thread looks likely to grow, us beginners are all seeking to get their favourite hardware up and running, much of it with MS driver disks. I have a Canon 9900F and a Umax Astra 1220U scanners neither of which are recognized by Xsane. I also await the delivery of Turboprint driver for my Canon i905D printer. Is there any useful source of downloadable drivers for these relatively common devices or driver conversion of the MS stuff into Linux? I have looked at Wine but this seems to be games oriented with few MS applications i.e. Office 2007 etc., Suggestions welcomed.

Colintivy..Hardy on a laptop.:confused:

---

### Post by Bucky Ball on 2008-08-07
> **jerryduk said:**
> Thanks I looked at XSANE but it doesn't see the scanner.

I see. Hmm ...

---

### Post by jerryduk on 2008-08-08
> **colintivy said:**
> Hi folks

This thread looks likely to grow, us beginners are all seeking to get their favourite hardware up and running, much of it with MS driver disks. I have a Canon 9900F and a Umax Astra 1220U scanners neither of which are recognized by Xsane. I also await the delivery of Turboprint driver for my Canon i905D printer. Is there any useful source of downloadable drivers for these relatively common devices or driver conversion of the MS stuff into Linux? I have looked at Wine but this seems to be games oriented with few MS applications i.e. Office 2007 etc., Suggestions welcomed.

Colintivy..Hardy on a laptop.:confused:

According to the SANE list of supported devices the UMAX should be OK but not the brother? [SANE]("http://www.sane-project.org/sane-mfgs.html#Z-UMAX")

---

### Post by SunnyRabbiera on 2008-08-08
Well if its a HP then you are luck as most of them work with linux, I know most models offer drivers for linux if you know where to look.

---

### Post by Bucky Ball on 2008-08-08
> **jerryduk said:**
> [COLOR=Red]Fixed - Installed printer as suggested by forest pixie then looked over the web for the scanner. Found something on Sourceforge - "HPLIP is an HP developed solution for printing, scanning, and faxing with HP inkjet and laser based printers in Linux" which enabled me to download and install software which works a dream and links to XSANE as suggested by Bucky Ball - Fixed my printer scanner in two hours on ubuntu. [/COLOR]

Hey, that is fantastic news, jerryduk! And nice tweaking. Glad to be of some assistance. The forums are a fantastic learning curve for everyone. Have fun with your explorations and don't forget to post again if you encounter any brick walls ... :)

ps: Another feature of Ubuntu is that if the printer is installed, it is installed 'globally' no screwing 'round trying to set it up in differenct programs. Also, I've heard there is a way of marking a thread [SOLVED], but not sure how. Maybe another member could let us know ...

---

### Post by Elfy on 2008-08-08
> ps: I've heard there is a way of marking a thread [SOLVED], but not sure. Maybe another member could let us know ...Thread tools - OP, mods and admin only can do it.

---

### Post by colintivy on 2008-08-25
Hi Jerrduk

You were quite right, UMAX was listed OK. The 1220U has been recognised and a copy of a test print from HP made. I found that the GUI much more complicated than the original Win from UMAX. The copy did not give a good white and, suprisingly showed a ghost image of the printing on the reverse of the original which was on some scrap paper that I had to hand. I must look to see if I can make adjustments to the set-up to get the balance right. Any advice?

colintivy :)

---

