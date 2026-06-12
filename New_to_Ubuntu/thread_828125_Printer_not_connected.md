---
title: "Printer not connected"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mancroft on 2008-06-13
Am trying to get my printer to work. In spite of the printer being connected to the computer, I get an error saying the printer is not connected. Here is the error printout: > Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fd0c0>,
 'cups_instance': None,
 'cups_queue': 'Stylus_D92',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20D92',
                       'printer-info': u'Stylus_D92',
                       'printer-is-shared': True,
                       'printer-location': u'john-desktop',
                       'printer-make-and-model': u'Epson Stylus Color PRO Foomatic/stcolor',
                       'printer-state': 4,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_D92'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'connecting-to-device'}
Page 4 (Print test page):
{'test_page_job_status': [(5, 'Stylus_D92', 'KDE Print Test'),
                          (6, 'Stylus_D92', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'connecting-to-device'}

Any ideas please?

---

### Post by wolfen69 on 2008-06-13
see [This]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_D92")

---

### Post by alienexplorers on 2008-06-13
Stupid questio but do you use USB 1.0 or 2.0....  The reason I asked is I have an old machine with USB 1.0 and my printer showed as connected, but did not print.  When I got a USB 2.0 card it started to work.  Really strange.....

---

### Post by mancroft on 2008-06-16
Thanks guys. I solved the problem:

see:

[http://kubuntuforums.net/forums/index.php?topic=3089184.msg106277](http://kubuntuforums.net/forums/index.php?topic=3089184.msg106277)

and eventually set it up using:

Printer Driver: Epson Stylus D68 - CUPS+Gutenprint v5.0.2

---

