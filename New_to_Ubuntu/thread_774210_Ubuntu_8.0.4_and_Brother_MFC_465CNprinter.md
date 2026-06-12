---
title: "Ubuntu 8.0.4 and Brother MFC 465CNprinter"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ratspom on 2008-04-29
Before I start I would just like to say hello to everyone on the forums. My main reason for joining is to tap into the wealth of knowledge that you all have regarding Linux and its different variations.

I have used computers and mainly ...."shush"  MS OS and software from the mid 80's and as such I'm very new to Linux and specifically Ubuntu 8.0.4. My problem is my Brother MFC  645cn printer. I download the LPR and Cups wrapper from the brother open source website and saved them to the desktop. 
Next I simply double clicked on each in turn starting with the LPR driver and then cups, ubuntu opened these folders with terminal and installed them for me. I then tried to print out a test page and nothing happened except that the printer LCD screen simply showed that it was reciving data and not printing the test page. Iused the help diagnostic tool and it simply reported what I have cut and pasted below

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8717a60>,
 'cups_instance': None,
 'cups_queue': 'MFC465CN',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/MFC-465CN',
                       'printer-info': u'MFC465CN',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Local Raw Printer',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 131076,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC465CN'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(4, u'Job completed.')],
 'test_page_job_id': [4],
 'test_page_job_status': [(4, 'MFC465CN', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}



basically does anyone know what I'm doing wrong. I also had a good look around the forum using the search tool for printer related problems but at this stage in my Ubuntu education its all a blur at the moment


Many Thanks 


Mac

---

