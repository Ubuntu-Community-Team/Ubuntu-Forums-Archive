---
title: "[SOLVED] printer won't work !"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Drakkor on 2008-09-23
It's an HP deskjet 845c and here's the debug output:

age 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x90f5aa0>,
 'cups_instance': None,
 'cups_queue': 'DESKJET_845C',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_845C?serial=CN19O1B096SX',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 845C',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP DeskJet 845C Foomatic/cdj670',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'other'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET_845C'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'other'}
Page 4 (Print test page):
{'test_page_job_status': [(1,
                           'DESKJET_845C',
                           'Michael, enjoy $50 Free Slot Play at Jackson Rancheria!'),
                          (3, 'DESKJET_845C', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'other'} :confused:
Edit: it's usb

---

### Post by cariboo on 2008-09-23
Have you used the HP setup tools to set up your printer?

The gui is available in the repositories, to install it, in a terminal type:

```
sudo apt-get install hplip-gui 
```

This should get you going as HP printers are well supported.

Jim

---

### Post by phidia on 2008-09-23
[Your printer]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C") is reported to work perfectly. Have you installed the hplip package?

How are you going about setting it up? Use the print manager from System > Administration > Printing.

---

### Post by Drakkor on 2008-09-23
HOORAY !! :D  It is working perfectly now, I printed the test page,and an
email, and it works great now ! Thanks, guys :)

---

