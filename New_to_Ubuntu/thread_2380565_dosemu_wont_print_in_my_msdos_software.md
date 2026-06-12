---
title: "dosemu wont print in my msdos software"
date: 2017-12-19
forum: New to Ubuntu
---

### Post by plozano on 2017-12-19
I have msdos program which I run from dosemu because currently im using ubuntu 12 32bit OS.. i can print in libre offices and our msdos program, now my problem is, after I upgrade it into ubuntu 14, i can print on documents but not anymore on our msdos program. any help will do.

P.S - Im newbie.

---

### Post by mastablasta on 2017-12-20
have you tried DOSBox instead? it's in the repositories and last version was made much later than dosemu.

---

### Post by Holger_Gehrke on 2017-12-20
DOSBox is aimed at running DOS Games and comes with absolutely NO support for printing whatsoever in standard builds, although there are some builds which do offer some. For running DOS applications that need to print, dosemu is the better choice. You should check the dosemu configuration in /etc/dosemu.conf or /etc/dosemu/dosemu.conf or (user-specific) in ~/.dosemurc for definitions that look like '$_lpt1 = lpr -l". Further details at [dosemu.org]("http://dosemu.org/docs/README/1.4/config.html#AEN312").

Holger

---

### Post by plozano on 2017-12-25
tried this one already. I'm just wondering, is this something to do with CUPS? because before at my ubuntu 12, after I install CUPS, it all works. but its a bit different on ubuntu 14.

---

