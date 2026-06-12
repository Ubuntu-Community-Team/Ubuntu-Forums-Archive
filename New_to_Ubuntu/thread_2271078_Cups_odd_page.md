---
title: "Cups odd page"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by elbambolo on 2015-03-27
Hi,
i'm new to this forum and new to Xubuntu.

I have a problem with my printer:
Lexmark E260 - USB

I have installed the last cups: 1.7.2 and i have installed the official lexmark driver for the printer.

the xUbuntu version is 14.04.1 LTS

Often happens that the printer block the job and print a row of characters like: éç2313fcrefèa234*-+7ASdasd="^^£$123V%£$"?$£=*"
and if i want print, i have to switch off and on the printer and re-print the document.
this routine happens 8-9 time a day!!!

I have tried to download the foomatic driver, but no change. 

Anyone have a hint or a tip's for solving this problem?
Thank's :)

---

### Post by Geoffrey_Arndt on 2015-03-27
Did you try Open Printing as source for drivers?  Note that they have driver compatible  for the E260, E260d, E260dn.

Download the "deb" file and install with either gdebi (is in repos), or via USC (ubuntu software center).

[http://www.openprinting.org/printer/Lexmark/Lexmark-E260](http://www.openprinting.org/printer/Lexmark/Lexmark-E260)

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)  (generic search page for all printers)

Note, you may have to purge existing drivers, and uninstall-reinstall printer  . . .

---

### Post by elbambolo on 2015-03-27
tanks for the reply,

I have tried to delete the printers, and after i have installed the driver from openprinting.
I have reinstalled the printer with the new driver and i have launched the printer test page. 
After this job, i have tried to print a 10 page from a web page.
until page 5 all ok... page 6 strange charters... and the printer is blocked :(

I have no idea... 
CUPS have the error log somewhere?
at the:
[https://127.0.0.1:631/admin/log/page_log](https://127.0.0.1:631/admin/log/page_log) 
i have only the job, without error.

any ideas?
thank you.

---

