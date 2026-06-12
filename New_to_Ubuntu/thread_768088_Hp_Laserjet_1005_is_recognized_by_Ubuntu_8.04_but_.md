---
title: "Hp Laserjet 1005 is recognized by Ubuntu 8.04 but doesn't work"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by allp on 2008-04-26
I've read what is written in the forums.

I've tried but it does not print and it was OK with Ubuntu 7.04

I can't understand what happens

This is the current status of the problem:

---------------
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x870cfc0>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_1005_series_',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1005_series?serial=0',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'ALLP',
                       'printer-make-and-model': u'HP LaserJet 1005 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1005_series_'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [18],
 'test_page_job_status': [(18, 'hp_LaserJet_1005_series_', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
------------------------

Thanks for your help

---

### Post by stchman on 2008-04-26
> **allp said:**
> I've read what is written in the forums.

I've tried but it does not print and it was OK with Ubuntu 7.04

I can't understand what happens

This is the current status of the problem:

---------------
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x870cfc0>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_1005_series_',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1005_series?serial=0',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'ALLP',
                       'printer-make-and-model': u'HP LaserJet 1005 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1005_series_'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [18],
 'test_page_job_status': [(18, 'hp_LaserJet_1005_series_', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
------------------------

Thanks for your help

You need to install the updated foo2zjs.

I have a tutorial on that.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

It covers Feisty and earlier and Gutsy.

If Hardy uses system-config-printer then usew the Gutsy script.  If Hardy uses gnome-cups-manager use the Feisty and earlier script.

---

### Post by allp on 2008-04-26
I eventually made it work. Look at the following link to find the solution:

[http://prdownloads.sourceforge.net/hplip/hplip-2.8.4.run](http://prdownloads.sourceforge.net/hplip/hplip-2.8.4.run)

Directions in Spanish here:

[http://www.ubuntu-es.org/index.php?q=node/86221](http://www.ubuntu-es.org/index.php?q=node/86221)

---

