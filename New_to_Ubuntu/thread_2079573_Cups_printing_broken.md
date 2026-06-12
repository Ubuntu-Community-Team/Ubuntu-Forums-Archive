---
title: "Cups printing broken"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by pvanonselen on 2012-11-02
I have a problem printing from my Ubuntu 12.10 install.

Initially printing to a Minolta 283 bizhub hanged the printer for some reason.

I used the linux driver suppied by Konica Minolta.

It workd in 11.10.  

Now I tried to install previous cups 1.5.4 instead.  I removed cups 1.6 and manually built 1.5.4 from sources.  This broke cups completely as it looked for folders that does not exist any more.

So removed cups and tried to install 1.6 again.

Now I am getting this error:
Unsupported format "application/vnd.cups-banner".

From the cups error log:
Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/KONICA-MINOLTA-bizhub-283) from localhost

How can I fix my cups?  Even my printers that was working now does not work.

---

### Post by zokej on 2012-11-02
I have this problem too. In 12.04 works OK, but in 12.10 not work.
In my opinion this problem with cups version 1.6.1, in cups version 1.5.3 all ok.
My printer is bizhub c203

---

### Post by Almoni111 on 2012-11-02
I'm not looking to create a hosting server. I want to create records to an existing network printer while I'm signed in via to my  Server 10.4 control line shell....

---

### Post by pvanonselen on 2012-11-04
How do I install cups 1.5.4 in Ubuntu 12.10?

Seems like this would solve my printing issue.

---

### Post by DomKM on 2012-11-08
Same problem with Ubuntu 12.10 and cups 1.6.1 and printer/MFP devices . Can someone provide a procedure to downgrade from cups 1.6.1 to 1.5.3?

---

### Post by talon42 on 2012-12-07
Just upgraded to 12.10.  Same issue with Konica Minolta mc5670.  It just prints blank pages.  HP printers seem fine.  Worked ok with 12.04.   Any resolutions?
these are both network printers.

---

### Post by Rick66 on 2012-12-18
I'm having a problem also since I switched to Ubuntu 12.10 from Lubuntu 12.04.   In short, our network KM Bizhub C220 printer just hangs when you send a print job.  Never had a problem when I was using Lubuntu 12.04 on my older machine.

---

### Post by CRMcMullen on 2013-01-07
Same here.  Ever since upgrading from 12.04 to 12.10 I've not been able to print to our KONICA-MINOLTA BizHub C25.  Worked fine before.  Now the printer just hangs and has to be reset.

---

### Post by Stir on 2013-01-11
I have the same problem 12.10. Can't print to anything on the network. I have 3 printers. One is a Canon 1023N shared over ethernet. Other is a Konica Minolta 2400W shared via a Win7 machine.

I only added the Canon currently to try to debug the problem. Here is my error log:

```
E [11/Jan/2013:16:30:23 -0500] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [11/Jan/2013:16:31:14 -0500] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_1023
W [11/Jan/2013:16:31:27 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id '1023-Gray..' already exists
W [11/Jan/2013:16:31:27 -0500] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-1023' already exists
E [11/Jan/2013:16:33:19 -0500] Unknown directive SystemGroup on line 3 of /etc/cups/cupsd.conf.
W [11/Jan/2013:16:33:19 -0500] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_1023
```

---

### Post by ubart on 2013-02-18
For LibrOffice on 12.10 I can get around this problem by selecting postscript as print format instead of pdf.

---

