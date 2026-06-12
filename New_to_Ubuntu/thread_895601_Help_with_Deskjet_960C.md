---
title: "Help with Deskjet 960C"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by haley1 on 2008-08-20
I'm trying to get an HP Deskjet 960C working with Hardy, it was working before with Breezy. The following error is reported, I'm not experienced enough to understand it however. Any help is appreciated. 

Page 1 (Choose printer): 
{'cups_dest': <cups.Dest object at 0x9f13c80>, 
 'cups_instance': None, 
 'cups_queue': 'DESKJET_960C', 
 'cups_queue_listed': True} 
Page 2 (Check printer sanity): 
{'cups_device_uri_scheme': u'usb', 
 'cups_printer_dict': {'device-uri': u'usb://HP/DESKJET%20960C?serial=MY11N1C03DRO', 
                       'printer-info': u'HEWLETT-PACKARD DESKJET 960C', 
                       'printer-is-shared': True, 
                       'printer-location': u'', 
                       'printer-make-and-model': u'HP DeskJet 960C Foomatic/hpijs, hpijs 2.8.2', 
                       'printer-state': 3, 
                       'printer-state-message': u'No %%BoundingBox: comment in header!', 
                       'printer-state-reasons': [u'connecting-to-device'], 
                       'printer-type': 135196, 
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET_960C'}, 
 'is_cups_class': False} 
Page 3 (Printer state reasons): 
{'printer-state-message': 'No %%BoundingBox: comment in header!', 
 'printer-state-reasons': 'connecting-to-device'} 
Page 4 (Print test page): 
{'test_page_attempted': True, 
 'test_page_completions': [(11, u'Job canceled.')], 
 'test_page_job_id': [11], 
 'test_page_job_status': [(11, 'DESKJET_960C', 'Test Page')], 
 'test_page_jobs_cancelled': True, 
 'test_page_successful': False} 
Page 5 (Printer state reasons): 
{'printer-state-message': '', 'printer-state-reasons': 'connecting-to-device'}

---

### Post by LowSky on 2008-08-20
HPLIP is installed to help with HP printers

System>Admin>HPLIP

if you need a newer version

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

---

### Post by alienexplorers on 2008-08-20
```
HP Deskjet 960c

Supported by HPLIP (requires HPLIP version 0.9.5 or later).

This information applies to these HP printer models:
Model Name
HP Deskjet 960c
HP Deskjet 960cse
HP Deskjet 960cxi
Summary of features available in various Linux distributions:
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
Debian	2.2	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	3.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	3.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0r0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0r1	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	5.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	lenny	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	lenny/sid	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	stable	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	testing	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	1.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	2.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	3.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	4.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5.92	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	6.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	6	Yes	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
Fedora	7	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	7.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	8.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	8	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	9	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	9.0	Yes	Yes	No	No	Yes	No	Yes	No	No
IGOS	1.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Linspire	5.0	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	9.1	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	9.2	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.0	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.2	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2006.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2007.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2007.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2008.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	6.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	6.5	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	7.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
PCLinuxOS	2006.0	Yes	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2006	Yes	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2007.0	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2007	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2008.0	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2008	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat	8.0	No	No	No	No	Yes	No	Yes	No	No
Red Hat	9.0	No	No	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	3.0	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	4.0	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	5.0	No	Yes	No	No	Yes	No	Yes	No	No
Slackware Linux	9.0	No	No	No	No	Yes	No	No	No	No
Slackware Linux	9.1	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.0	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.1	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.2	No	No	No	No	Yes	No	No	No	No
SUSE Linux	9.0	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.1	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.2	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.3	No	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
SUSE Linux	10	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.0	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.1	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.2	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.3	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	11.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	5.04	No	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	5.1	No	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	6.06	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	6.10	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	7.04	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	7.10	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	8.04	Yes	Yes	No	No	Yes	No	Yes	No	No
```

---

### Post by haley1 on 2008-08-20
Thanks all, I'll give it a try.

---

