---
title: "My HP LaserJet 5 printer has stopped working [bug report included]"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by silent contender on 2008-09-15
Like the thread said my printer has stopped working.  The printer did working in Ubuntu (still works in Windows).  It is connected to the home networking (I pinged it and had a response).

The bug report the Printing Troubleshoot outputted (it's for the test page):

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x94a7f00>,
 'cups_instance': None,
 'cups_queue': 'LaserJet5',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://192.168.0.103:9100',
                       'printer-info': u'HP LaserJet (B&W)',
                       'printer-is-shared': True,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'HP LaserJet 5 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135196,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet5'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [18],
 'test_page_job_status': [(18, 'LaserJet5', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': "recoverable: Network host '192.168.0.103' is busy; will retry in 25 seconds...",
 'printer-state-reasons': 'connecting-to-device'}

---

### Post by bmac on 2008-09-16
You may try and install the HPLIP print driver. It solved my HP laser problems....

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hopr this helps....

---

