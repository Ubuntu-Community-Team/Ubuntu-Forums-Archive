---
title: "How to cancel a print job in open office"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by rosswmcgee on 2008-08-20
How to cancel a print job in open office. I just keeps repeating the same print job. I have shut down every thing unplugged the printer put every thing back and still can not stop it, and then the printer jams and the whole cycle starts again.

---

### Post by LowSky on 2008-08-20
you dont need to start a new thread, to help... try opening a terminal and typing this command

lprm (to cancel a print job)

[QUOTE=amohanty]
lpq (to view the printer queue)
lprm (to cancel a print job)

Technically stopping the print job should stop printing after whatevers in the printer's buffer is done. Instead of restarting try restarting the cupsys service (if its an HP printer the hplip service too) using
sudo /etc/init.d/cupsys restart
[http://ubuntuforums.org/showthread.php?t=400881](http://ubuntuforums.org/showthread.php?t=400881)
[/QUOTE]


dont forget to search

---

### Post by rosswmcgee on 2008-08-21
I found by going to the printer and clicking on help and following next next it gave me the cancel print jobs option. Problem solved thanks for the help. I was going nuts.

---

