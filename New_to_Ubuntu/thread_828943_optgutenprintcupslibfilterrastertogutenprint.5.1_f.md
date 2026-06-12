---
title: "/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.1 failed"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by mancroft on 2008-06-14
I solved the problem below:

see:

[http://kubuntuforums.net/forums/index.php?topic=3089184.msg106277](http://kubuntuforums.net/forums/index.php?topic=3089184.msg106277)

and eventually set it up using:

Printer Driver: Epson Stylus D68 - CUPS+Gutenprint v5.0.2

> {'printer-state-message': '/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.1 failed',
 'printer-state-reasons': 'none'}

I'm slowly going mad trying to get my perinter to work. Any idea what the above message means?

> Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x9bb3740>,
 'cups_instance': None,
 'cups_queue': 'Stylus_D92',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'epson',
 'cups_printer_dict': {'device-uri': u'epson:/dev/usb/lp0',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'john-desktop',
                       'printer-make-and-model': u'Epson Stylus D92 - CUPS+Gutenprint v5.1.98.2',
                       'printer-state': 3,
                       'printer-state-message': u'/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.1 failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8425484,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_D92'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.1 failed',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(52, 'Stylus_D92', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.1 failed',
 'printer-state-reasons': 'none'}
Page 6 (Check user sanity): going mental


---

