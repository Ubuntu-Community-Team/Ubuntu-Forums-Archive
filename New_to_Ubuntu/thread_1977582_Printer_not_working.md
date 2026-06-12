---
title: "Printer not working"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Bigjack08 on 2012-05-10
Hello all I have a Brother DCP 385C printer/scanner; a Compaq Presario desktop PC and Samsung R530 laptop (both now running ubuntu 12.04.  Anyone any ideas for getting my printer working, I have been to Brother website and they have no drivers (they have one for Debian 4 but software centre would not load reporting it to be a poor package. Just a niggling little problem I hope?

---

### Post by plucky on 2012-05-10
> **Bigjack08 said:**
> Hello all I have a Brother DCP 385C printer/scanner; a Compaq Presario desktop PC and Samsung R530 laptop (both now running ubuntu 12.04.  Anyone any ideas for getting my printer working, I have been to Brother website and they have no drivers (they have one for Debian 4 but software centre would not load reporting it to be a poor package. Just a niggling little problem I hope?

See [Brother Printer Drivers for Linux](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Download and install both the lpr and cupswrapper .deb files.
Also read the instructions given on the Brother Website.


Good Luck

---

### Post by gordintoronto on 2012-05-10
It might be a lot simpler than that.

What is your printer attached to?

I have a Brother laser attached to my router. To set it up in Ubuntu 12.04, I run Printing, Add, Network Printer, wait a few seconds, click on my printer, forward and OK until it works. Ubuntu looks after all the other stuff.

---

### Post by Bigjack08 on 2012-05-11
Thanks Plucky and Gord; the printer situation is now sorted on both my desktop and laptop with a combination of your advice.

I downloaded the two .deb files as suggested and loaded them via the software centre ignoring the warnings.  The lps file has to be run from the Terminal. Then following the advice to plug in the printer when computer on and using the Add Printer option both computers found the new drivers and both now work. Result.

---

