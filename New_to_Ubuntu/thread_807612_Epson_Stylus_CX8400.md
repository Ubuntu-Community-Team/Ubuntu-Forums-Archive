---
title: "Epson Stylus CX8400"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by g45model21 on 2008-05-26
I just got an Epson Stylus CX8400 for my birthday and I don't know how to install it.  How do I do that?

---

### Post by perce on 2008-05-26
> **g45model21 said:**
> I just got an Epson Stylus CX8400 for my birthday and I don't know how to install it.  How do I do that?

Your printer should be supported, and maybe it's even plug and play. Have you tried to plug it in and turn it on? what happens? If nothing happens, you can go to the printer configuration menu under System > Administration it's straightforward to use.

---

### Post by Maestro23 on 2008-05-26
And here is the entry for your printer at OpenPrinting.org 

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX8400](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX8400)

---

### Post by perce on 2008-05-26
> **Maestro23 said:**
> And here is the entry for your printer at OpenPrinting.org 

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX8400](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX8400)

I checked there that the printer is supported, but I didn't point him to that page because I don't want him to download the driver from that page and try to install it (in the Windows way).

---

### Post by EtniesBMX on 2008-06-18
Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800.

To make scanning work, go to menu>accesories>terminal, and type:
Code:

```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner

---

### Post by Canadian_Psycho on 2008-09-07
I tried your fix Etnies using the older drivers and it did work to get printing going.  However, trying that command to get scanning to work rendered me a message saying "E: Couldn't find package lisbane-extra"

Any ideas?

Cheers

---

### Post by Canadian_Psycho on 2008-09-07
oops, never mind.  I figured it out.  There's a letter missing.

The command should be

```
sudo apt-get install libsane-extras
```

Cheers

---

### Post by daveleo on 2008-09-16
EtniesBMX .... thanks for the CX8400 steps.

but .... now XSANE is locking up at the "searching for drivers" window.... this happens both from GIMP and when running XSANE as a standalone.

i am this one step away from total ubuntu conversion !!!

any additional ideas???

---

### Post by Etaoin Shrdlu on 2009-12-20
[SIZE=2]There are drivers [here](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) that might work for Epson all-in-ones. I have a CX7800 and got the scanner working with a driver from that site.[/SIZE]

---

