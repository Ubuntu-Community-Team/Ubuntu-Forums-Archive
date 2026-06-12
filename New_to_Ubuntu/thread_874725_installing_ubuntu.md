---
title: "installing ubuntu"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-30
Hiya,

I got few old PCs with ubuntu installed.I wish to do a fresh re-install of ubuntu. 
I inserted the iso image cd,but all the machines fail to detect it and goes to the desktop screen of the previous ubuntu installed on them.I tried F1,F2,DEl etc to get to BIOS setup to check whether boot from cd is enabled....but i cant access the Bios setup as well,every time i reboot,it takes me to the ubuntu login screen.... What am i missing here?Plz help

Cheers
David

---

### Post by gvartser on 2008-07-30
1) Are you sure that your ubuntu cd is bootable?

2) What is the brand and model of your HW? (google can tell you how to get into the bios.)

/g

---

### Post by jame86 on 2008-07-30
This does sound like the bios is not set to boot from CD.

I would suggest watching to boot screen carefully, and either looking for the command to get into the bios (sorry dont understand if you meant you couldnt get to it, or not!), or to look for a "F* to see list of boot devices".

Obviously check that the "iso disk" is a burnt copy of the iso, not just the iso on the disk (no offence ment!), and that it is not burnt to a rw disk. As some older systems wont boot from a CD-RW!

Otherwise let us know!

Damingo,

---

### Post by sharks on 2008-07-30
first remove ur ubuntu cd and then reboot and go to BIOS and change ur BIOS settings.

---

### Post by gvartser on 2008-07-30
> **sharks said:**
> first remove ur ubuntu cd and then reboot and go to BIOS and change ur BIOS settings.

He tried that but does not how to get into the bios. Non of the stuff he tried worked, but with the correct brand and model of the computer its easy to find out.

---

### Post by coffeecat on 2008-07-30
You have several PCs that you were unable to get into the BIOS with? The key varies from manufacturer to manufacturer, but you were unlucky that none responded to F2 or del.

You're probably better off going to the manufacturer's website rather than googling. You'll have to search the website for the manual because they'll all be obsolete models. Or, better, look on the motherboard m'facturer's website. If you run 'sudo lshw' from a terminal (you may have to install lshw first - can't remember whether it comes in a default install), the motherboard model is **sometimes** given near the beginning of the output.

---

