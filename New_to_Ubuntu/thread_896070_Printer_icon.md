---
title: "Printer icon"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by rosswmcgee on 2008-08-20
where is my printer icon?

---

### Post by LowSky on 2008-08-20
IDK? behind the couch?


seriously what are you talking about?

I posted this in your other thread.
you dont need to start a new thread, to help... try opening a terminal and typing this command

lprm (to cancel a print job)

[QUOTE=amohanty]
lpq (to view the printer queue)
lprm (to cancel a print job)

Technically stopping the print job should stop printing after whatevers in the printer's buffer is done. Instead of restarting try restarting the cupsys service (if its an HP printer the hplip service too) using
sudo /etc/init.d/cupsys restart
[http://ubuntuforums.org/showthread.php?t=400881](http://ubuntuforums.org/showthread.php?t=400881)
[/QUOTE]

---

### Post by Cheesehead on 2008-08-20
No printer icon...why would you need one?

Administer your printer(s) though cups. Several GUIs are available (look in your Applications --> Settings for 'Printers' or something similar.

You can also talk to cups directly by opening your web browser and typing 'localhost:631' into the URL bar; that's how I do it.

---

### Post by rosswmcgee on 2008-08-21
I found it ion sys admin, need it to get help in cancelling print job. Thanks!

---

