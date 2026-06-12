---
title: "Can't get printer to work (epson stylus dx4850)"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by gerben1 on 2008-07-23
Hi,

I am trying to get the Epson Stylus DX8450 to work. I followed this tutorial:
[http://hivernal.org/static/computing/hardware/epson-dx8450.en.html](http://hivernal.org/static/computing/hardware/epson-dx8450.en.html)
(basically just installing pipslite-cups and pipslite packages)

Anyways after I had done so, the printer seems to be installed fine and I can see it in System->Administration->Printing and also via the web interface [http://localhost:631](http://localhost:631). 

I can print test pages from both those configuration utilities, but I cannot print anything from any program. 

This is what happens:
After I click print the print job gets stopped almost immediately, see the screenshot.

this is what is in /var/log/cups/error-log:
```

E [23/Jul/2008:19:54:16 +0200] PID 6688 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:55:57 +0200] PID 6741 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:56:17 +0200] [Job 17] Job stopped due to filter errors.
E [23/Jul/2008:19:56:42 +0200] PID 6816 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:56:43 +0200] [Job 18] Job stopped due to filter errors.
E [23/Jul/2008:19:57:06 +0200] PID 6827 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:57:06 +0200] [Job 19] Job stopped due to filter errors.

```

---

### Post by gerben1 on 2008-07-23
Anybody?

I think it is a problem with file permissions somehow, but can't figure it out...

/var/log/cups/error-log```

E [23/Jul/2008:16:28:02 +0200] Resume-Printer: Unauthorized
E [23/Jul/2008:17:27:36 +0200] Pause-Printer: Unauthorized
E [23/Jul/2008:17:27:52 +0200] Resume-Printer: Unauthorized
E [23/Jul/2008:17:34:05 +0200] [Job 3] No %%BoundingBox: comment in header!
E [23/Jul/2008:17:42:22 +0200] Pause-Printer: Unauthorized
E [23/Jul/2008:17:43:09 +0200] Resume-Printer: Unauthorized
E [23/Jul/2008:17:54:30 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:18:05:17 +0200] PID 7583 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:18:05:17 +0200] [Job 6] Job stopped due to filter errors.
E [23/Jul/2008:18:06:05 +0200] PID 7590 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:18:06:06 +0200] [Job 7] Job stopped due to filter errors.
E [23/Jul/2008:18:20:14 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:18:57:46 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:19:02:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [23/Jul/2008:19:02:19 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:19:03:29 +0200] PID 6973 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:03:30 +0200] [Job 10] Job stopped due to filter errors.
E [23/Jul/2008:19:03:43 +0200] PID 6980 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:03:44 +0200] [Job 10] Job stopped due to filter errors.
E [23/Jul/2008:19:06:30 +0200] PID 6240 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:06:44 +0200] [Job 11] Job stopped due to filter errors.
E [23/Jul/2008:19:07:08 +0200] PID 6329 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:07:09 +0200] [Job 11] Job stopped due to filter errors.
E [23/Jul/2008:19:10:14 +0200] PID 6409 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:10:15 +0200] [Job 12] Job stopped due to filter errors.
E [23/Jul/2008:19:12:20 +0200] CUPS-Set-Default: Unauthorized
E [23/Jul/2008:19:12:28 +0200] cupsdAuthorize: Empty Basic username!
E [23/Jul/2008:19:12:28 +0200] CUPS-Set-Default: Unauthorized
E [23/Jul/2008:19:25:29 +0200] Pause-Printer: Unauthorized
E [23/Jul/2008:19:26:00 +0200] Resume-Printer: Unauthorized
E [23/Jul/2008:19:26:12 +0200] PID 6665 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:26:13 +0200] [Job 13] Job stopped due to filter errors.
E [23/Jul/2008:19:33:06 +0200] CUPS-Delete-Printer: Unauthorized
E [23/Jul/2008:19:33:06 +0200] CUPS-Delete-Printer: Unauthorized
E [23/Jul/2008:19:40:25 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:19:41:08 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:19:43:39 +0200] CUPS-Set-Default: Unauthorized
E [23/Jul/2008:19:43:56 +0200] PID 7080 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:43:58 +0200] [Job 15] Job stopped due to filter errors.
E [23/Jul/2008:19:54:16 +0200] PID 6688 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:55:57 +0200] PID 6741 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:56:17 +0200] [Job 17] Job stopped due to filter errors.
E [23/Jul/2008:19:56:42 +0200] PID 6816 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:56:43 +0200] [Job 18] Job stopped due to filter errors.
E [23/Jul/2008:19:57:06 +0200] PID 6827 (/usr/lib/cups/filter/rastertopips) stopped with status 8!
E [23/Jul/2008:19:57:06 +0200] [Job 19] Job stopped due to filter errors.
E [23/Jul/2008:20:48:01 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:20:48:10 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:22:06:32 +0200] Pause-Printer: Unauthorized
E [23/Jul/2008:22:09:12 +0200] CUPS-Delete-Printer: Unauthorized
E [23/Jul/2008:22:47:31 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:22:48:35 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [23/Jul/2008:22:49:39 +0200] PID 10948 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:22:49:40 +0200] [Job 21] Job stopped due to filter errors.
E [23/Jul/2008:22:55:41 +0200] PID 11056 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:22:55:42 +0200] [Job 21] Job stopped due to filter errors.
E [23/Jul/2008:22:55:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [23/Jul/2008:22:55:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [23/Jul/2008:23:06:22 +0200] PID 11255 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:23:06:23 +0200] [Job 21] Job stopped due to filter errors.
E [23/Jul/2008:23:08:50 +0200] Purge-Jobs: Unauthorized
E [23/Jul/2008:23:09:22 +0200] PID 11315 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:23:09:23 +0200] [Job 21] Job stopped due to filter errors.
E [23/Jul/2008:23:10:57 +0200] PID 11344 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:23:10:58 +0200] [Job 21] Job stopped due to filter errors.
E [23/Jul/2008:23:12:30 +0200] PID 11371 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:23:12:31 +0200] [Job 22] Job stopped due to filter errors.
E [23/Jul/2008:23:15:34 +0200] PID 11423 (/usr/lib/cups/filter/pipslite-wrapper) stopped with status 8!
E [23/Jul/2008:23:15:35 +0200] [Job 23] Job stopped due to filter errors.
```

---

### Post by ramjet_1953 on 2008-07-23
This link may be of use to you:

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX4850](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX4850)

Also, [COLOR="Blue"]TurboPrint[/COLOR] list your printer as being supported.
Here is a link:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

TurboPrint isn't free, but you can download a demo version first, to check that it works OK for you.

Regards,
Roger :cool:

---

### Post by gerben1 on 2008-07-24
Thanks, I didn't know about Turboprint. I tried it out and it works very nice, great options too, just unfortunate that it is so expensive.

If you want all the options, which would be great, you'll have to buy "Turboprint Studio" for 60 euros (just a little less than the printer costs), alternatively you can buy a version with less options for 30 euros.

Anyways I will be using it for at least the next 30 days, thanks again for the tip.

---

