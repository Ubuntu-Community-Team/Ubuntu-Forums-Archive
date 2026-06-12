---
title: "Printing error Dell 1320c Laser"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by ranger_cole on 2008-05-07
I am getting, in 8.04, a cups server error when I try to print to a dell 1320c laser printer.  It also says client error document format not supported when I try to print a test page.
Here is the dump from the printing troubleshooting wizard::confused:



Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fa8a0>,
 'cups_instance': None,
 'cups_queue': 'Color_Laser_1320c',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Dell/Color%20Laser%201320c',
                       'printer-info': u'Dell Color Laser 1320c',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Generic text-only printer',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135172,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Color_Laser_1320c'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_status': [],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by Sef on 2008-05-07
Check out [Openprinting.org]("http://openprinting.org/show_printer.cgi?recnum=Dell-1320c_color_laser").

---

### Post by ranger_cole on 2008-05-07
Thanks for the link.  Here is the file which i downloaded to my desktop.

Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm

I open a terminal window and get
jaypugh@jaypugh-desktop:~$ 
I then type according to instructions

 rpm -Uvh Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm
I get the following message:
 failed: No such file or directory
I am unable to install the printer.

---

