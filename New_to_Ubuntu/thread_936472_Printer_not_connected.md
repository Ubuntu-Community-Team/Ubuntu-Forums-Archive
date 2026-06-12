---
title: "Printer not connected"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by bobheaps on 2008-10-02
I have been running 8.04 for a few weeks now. I was able to use the printer psc1310 but it no longer works. I get a message suggesting it may not be connected. I have been tinkering with networks trying to get my laptop wirelessly connected and may have disturbed something. the following is the output from printer troubleshooter
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8e794c0>,
 'cups_instance': None,
 'cups_queue': 'psc_1310_series_',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/psc_1310_series?serial=MY4ADCC473O2',
                       'printer-info': u'hp psc 1310 series ',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP 2000C Foomatic/pcl3',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 12300,
                       'printer-uri-supported': u'ipp://localhost:631/printers/psc_1310_series_'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(158, u'Job completed.')],
 'test_page_job_id': [158],
 'test_page_job_status': [(158, 'psc_1310_series_', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Can anyone help me?

---

### Post by frank002 on 2008-10-02
Go to System>Administration>printers. See if the printer is still there.  You might want to uninstall it and reinstall it.

---

### Post by bobheaps on 2008-10-03
> **frank002 said:**
> Go to System>Administration>printers. See if the printer is still there.  You might want to uninstall it and reinstall it.

I have removed and re-installed, disconnected & reconnected printer, and shutdown and restarted computer to no avail. The printer did work at one time but not now. I must have done something whilst tinkering - I recently set up wireless on a laptop and also synchronized the desktop and laptop. Is it possible I did something then?

---

### Post by frank002 on 2008-10-03
Have you checked to see if your usb port is ok?  Other than that I cannot think of anything else. If I do, I'll post it here.

---

