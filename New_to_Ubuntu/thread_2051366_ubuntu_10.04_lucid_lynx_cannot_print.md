---
title: "ubuntu 10.04 lucid lynx cannot print"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by desertoasis on 2012-09-01
Have a BIG problem and I'm about as much of an absolute beginner as you can find.  Had problem with software (Comodo and ZoneAlarm) clashing when I had Comodo problems, uninstalled, then tried to install ZoneAlarm.  My computer froze.  Didn't know they were incompatible and that could happen.   Wouldn't go beyond the boot to the Toshiba page (I have a Toshiba Satellite M115 S4049 laptop with XP installed.)  So installed a dual boot Lucid Lynx using a CD from a book at the public library.  It runs fine, except somehow it will not print.  Probably I goofed.  When I installed the ubuntu, it came with Open Office and so forth.  I have a very old HP Deskjet 540.  It ran like gangbusters with Windows, but now this.    Bought an HP 4620 because HP is linux friendly, has help, drivers, etc. It worked fine for a while.  I went to HP forums, but got no help.  I am also using WineHQ.  That helps, but I don't know what to do.  Someone suggested uninstalling Open Office.  Any thoughts would be most appreciated.  But please, step by step.

---

### Post by roger_1960 on 2012-09-01
Hi

Have you installed HPLIP Toolbox from the software center?  If not, try it next.

---

### Post by desertoasis on 2012-09-01
I didn't have HPLIP, but I just installed it.  Thank you so  much.  What's next?

---

### Post by sersang on 2012-09-01
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

> [B][SIZE=2]Ubuntu 10.04 supplies HPLIP 3.10.2 and it does  not support your printer.

**You must download and install HPLIP in order to use your printer with Ubuntu 10.04.**[/SIZE][/B]



Try the newer version of hplip. You can download from the link.

---

### Post by desertoasis on 2012-09-01
Sorry.  I wrote the wrong thing.  I downloaded HPLIP Tool Box as Roger_1960 asked me to.   My printer did work originally, but it stopped.  So, while I respect your thoughts, sersang, I'll wait a bit for that to see what happens next.  I will remember what you said though.  Actually, I messed with the connection (after it stopped printing) thinking that might help.  Someone had suggested that, so it may be a little bit more than just the type of printer as opposed to maybe also a connection problem.  Not sure.  But thanks to you both.  I'm listening. B-)

---

### Post by anewguy on 2012-09-02
If by WineHQ you mean wine, then you need to know that you can't install Windows drivers there for a device you want to use in Linux.  You actually need the Linux support package - that's why roger_1960 had you download the HPLIP things.

I haven't looked, but it's possible that if you downloaded a newer version of HPLIP it may not be compatible with 10.04 - that's an old release.

---

### Post by mastablasta on 2012-09-02
after installing Hplip you need to add the printer. 

oh and 540 works perfectly in Ubuntu 10.04.

---

### Post by newb85 on 2012-09-02
Another thought:  you described it as a "very old" printer.  Make sure you're not plugging a USB1.0 device into a USB3.0 port.  I found out the hard way that the two aren't necessarily compatible.  (1.0 & 2.0 are compatible, and 2.0 & 3.0 are compatible, but the standards don't require 1.0 and 3.0 to be.)

---

