---
title: "printer is useless"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Drakkor on 2008-05-16
hp deskjet 845c, just spewes out paper, with gobbledegoop on the top,until I just have to unplug it !!

---

### Post by Raccoon1400 on 2008-05-16
Tell us more. What driver are you using?
Google the printer type and ubuntu. that's how I got my dell printer working.

---

### Post by Aearenda on 2008-05-16
Definitely sounds like a driver issue. And are you printing from Ubuntu or a Windows PC over the net? I've seen this happen when Samba was not told to use raw mode for printing from Windows PCs.

---

### Post by Drakkor on 2008-05-16
yeah,tried that,but after 9  pages of gobbledegoop on the top horizontaly,and the side vertically , I just unplugged the printer to stop it !! :(

---

### Post by Drakkor on 2008-05-16
Installed the "recommended" driver, but still it's shite !

---

### Post by Aearenda on 2008-05-16
Did you clear the print queue of old jobs before changing driver? Maybe it is still trying to print an old job with the wrong settings.

Have you tried a CUPS test print?

---

### Post by Drakkor on 2008-05-16
yeah,I tried the "test printing" same thing.

---

### Post by Aearenda on 2008-05-16
This printer should 'just work' with Ubuntu. [http://hplip.sourceforge.net/models/deskjet/deskjet_845c.html](http://hplip.sourceforge.net/models/deskjet/deskjet_845c.html)

1. What steps have you taken to try to fix it so far?
2. Did you make sure the print queue was empty of old stuff? CUPS retries failed jobs.
3. Does it still work with Windows?

---

### Post by Drakkor on 2008-05-16
3.Works with Vista
2.Printer queue is empty
1.Installed (recommended drivers}
I don't really want to go through 50 sheets of  paper to test all the different drivers !

---

### Post by Aearenda on 2008-05-16
:-) I always feed the same piece of paper in 50 times!

The recommended driver should work, regardless. 

Anything in /var/log/cups/access_log or /var/log/cups/error_log?
Has this condition persisted over a reboot (to clear hardware weirdness, not for Linux)?
Can't think of much else to try.

---

### Post by Drakkor on 2008-05-17
Got this in the error log:
E [16/May/2008:18:58:11 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [16/May/2008:18:58:43 -0700] [Job 3] No %%BoundingBox: comment in header!\

But in the access log got:

localhost - - [16/May/2008:04:55:30 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:06:53:45 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:54:05 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:55:02 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:55:02 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:55:02 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:06:55:37 -0700] "POST /printers/DESKJET_845C HTTP/1.1" 200 140199 Print-Job successful-ok
localhost - - [16/May/2008:06:55:37 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:06:55:38 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:06:55:38 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:06:55:40 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:06:56:10 -0700] "POST /jobs/ HTTP/1.1" 200 141 Cancel-Job successful-ok
localhost - - [16/May/2008:06:56:10 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:07:15:42 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:07:15:58 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:07:23:49 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:07:24:04 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:07:39:55 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:07:40:13 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:08:39:24 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:08:39:40 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:08:42:55 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:08:42:55 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:08:42:55 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:09:38:49 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:09:39:03 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:10:30:33 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:10:30:49 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:10:39:56 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:10:40:11 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:13:19:40 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:13:19:40 -0700] "POST / HTTP/1.1" 200 419 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:13:19:40 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:18:37:19 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:18:37:37 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:18:56:35 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:18:56:35 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:18:56:35 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:18:57:15 -0700] "POST / HTTP/1.1" 200 411 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:18:57:14 -0700] "POST / HTTP/1.1" 200 2339 CUPS-Get-Devices -
localhost - - [16/May/2008:18:57:16 -0700] "POST / HTTP/1.1" 200 1394186 CUPS-Get-PPDs -
localhost - - [16/May/2008:18:58:04 -0700] "POST / HTTP/1.1" 200 18730 CUPS-Get-PPD -
localhost - - [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 401 19001 CUPS-Add-Modify-Printer successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 200 19001 CUPS-Add-Modify-Printer successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 200 129 Resume-Printer successful-ok
localhost - - [16/May/2008:18:58:11 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 200 129 CUPS-Accept-Jobs successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 200 166 CUPS-Add-Modify-Printer successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST /admin/ HTTP/1.1" 200 147 CUPS-Add-Modify-Printer successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - root [16/May/2008:18:58:11 -0700] "GET /ppd/DeskJet_845C2.ppd HTTP/1.1" 200 18525 - -
localhost - root [16/May/2008:18:58:11 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:16 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:40 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:18:58:40 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:18:58:40 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:43 -0700] "POST /printers/DESKJET_845C HTTP/1.1" 200 153886 Print-Job successful-ok
localhost - - [16/May/2008:18:58:43 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:43 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:44 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:18:58:44 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:18:58:48 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:19:00:08 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:19:00:08 -0700] "POST /jobs/ HTTP/1.1" 200 141 Cancel-Job successful-ok
localhost - - [16/May/2008:19:00:08 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [16/May/2008:19:00:08 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:19:08:18 -0700] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [16/May/2008:19:08:18 -0700] "GET /ppd/DESKJET_845C.ppd HTTP/1.1" 200 42958 - -
localhost - - [16/May/2008:19:08:18 -0700] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [16/May/2008:19:08:34 -0700] "POST / HTTP/1.1" 200 1394186 CUPS-Get-PPDs -
localhost - - [16/May/2008:20:34:19 -0700] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok

---

### Post by Aearenda on 2008-05-17
CUPS thinks it's working. Assuming the 'persists over reboot' answer is 'yes', then the next thing I would do is to delete the printer from CUPS, then do ```
sudo /etc/init.d/cupsys restart
```and add the printer in again. If that doesn't work, I'm stumped!

---

### Post by nicedude on 2008-05-17
Heres a link to what driver you should be using with this printer
[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C)

Your printer works fully in linux with the correct driver, you are a lucky person as mine is actually a brick :-(

---

### Post by Sef on 2008-05-17
> Click the link in my signature below that says linux printers to go to the website with lists of printers that work in linux  

It should work OOTB (Out of the box.)  The [HPLIP site]("http://hplip.sourceforge.net/models/deskjet/deskjet_845c.html") has it working OOTB.


Drakkor: Did you try the printer before you installed any of the drivers for it?  My PSC simply works; no need to install anything.

---

### Post by Drakkor on 2008-05-17
> Drakkor: Did you try the printer before you installed any of the drivers for it? My PSC simply works; no need to install anything.
Yeah,actually I did, seems I just have to boot  to Vista to get my printing done :(

---

### Post by Aearenda on 2008-05-17
I think we all know it should work out of the box, but clearly this one doesn't :-)

Drakkor, did you try removing it and then adding it again as suggested in post 12?

---

### Post by Drakkor on 2008-05-17
Yeah,Aearenda tried that,thanks for the try,but no dice yet.

---

### Post by Aearenda on 2008-05-17
I expect you've tried this too, but we're clutching straws here - have you unplugged the printer from the mains and the computer, left it for a minute, then plugged it back in?

After doing this, take a look at 'dmesg' and see if there is anything odd in the output near the end concerning the printer.

---

### Post by ramjet_1953 on 2008-05-17
Check out this link:

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C)

This printer is fully supported under Linux.

Regards,
Roger :cool:

---

### Post by Aearenda on 2008-05-17
ramjet_1953: can you please suggest how we might work out what is wrong with it then?

---

### Post by ramjet_1953 on 2008-05-17
Is this printer plugged into a root USB port?

Sometimes USB devices don't like being operated through a hub.

Regards,
Roger :cool:

---

### Post by arden667 on 2008-05-18
You know, I tried to use my hp 845c for the first time this morning and had the exact same problem - printed lines of junk until I unplugged it, and I got the same error message and all.  Hope we can get this figured out... I've had such good luck with my hardware so far!

---

### Post by Aearenda on 2008-05-18
I suggest you log a bug report in Launchpad. See [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) for instructions on what to log, and use the output from the "Printing bug info" script referred to on that page. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) tells how to report a bug (ignore the apport section, look at "Filing bugs at Launchpad.net").

---

### Post by arden667 on 2008-05-18
I don't know if this will work for you, but I downloaded the HPLIP automatic installer and followed their directions ([http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)) and it fixed everything up for me with no trouble at all.  Yay!

---

### Post by Aearenda on 2008-05-18
Their version is 2.8.5, and it's 2.8.2 in Ubuntu. 

I still think a bug report would be useful, with the added info that 2.8.5 fixes the problem, so that the devs know they need to integrate it soon. You cannot assume that any developers have the time to read these forums.

---

