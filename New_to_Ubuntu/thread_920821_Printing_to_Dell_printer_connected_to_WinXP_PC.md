---
title: "Printing to Dell printer connected to WinXP PC"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-15
Another one for you.

I have Dell printer connected to a Dell PC, running WinXP.

I have another Dell PC which is now purely Ubuntu.  I am trying to print to the printer, but with no luck.

Everything I've done points to the printer being available, and the troubleshooting I've done produced the following report:

Page 1 (Choose printer): 
{'cups_dest': <cups.Dest object at 0x8b7cb20>, 
 'cups_instance': None, 
 'cups_queue': '1100', 
 'cups_queue_listed': True} 
Page 2 (Check printer sanity): 
{'cups_device_uri_scheme': u'smb', 
 'cups_printer_dict': {'device-uri': u'smb://HOME/OFFICE/Office', 
                       'printer-info': u'1100', 
                       'printer-is-shared': True, 
                       'printer-location': u'OFFICE', 
                       'printer-make-and-model': u'Dell 1100, 1.1.0', 
                       'printer-state': 3, 
                       'printer-state-message': u'', 
                       'printer-state-reasons': [u'none'], 
                       'printer-type': 176196, 
                       'printer-uri-supported': u'ipp://localhost:631/printers/1100'}, 
 'is_cups_class': False} 
Page 3 (Printer state reasons): 
{'printer-state-message': '', 'printer-state-reasons': 'none'} 
Page 4 (Print test page): 
{'test_page_attempted': True, 
 'test_page_completions': [(7, u'Job completed.')], 
 'test_page_job_id': [7], 
 'test_page_job_status': [(7, '1100', 'Test Page')], 
 'test_page_successful': False} 
Page 5 (Printer state reasons): 
{'printer-state-message': '', 'printer-state-reasons': 'none'} 

Do I need to install the Dell printer drivers on the Linux PC (would they work anyway?).
As previously mentioned, Ubuntu can 'see' the printer on the network, and therefore the other PC is switched on.

Is there anyone brave enough to tackle this problem.

I'm running 8.04, by the way - if that helps.  Also, the printer is not an 1100 as the report states, but the actual model is not available to choose from (which is why I think drivers might be necessary!!)

Help, once again, much appreciated.  And then maybe my children will stop pestering me to print stuff out for them.

Thanks in anticipation.

---

### Post by Thelasko on 2008-09-15
If I recall correctly, your "Dell" printer is actually a re-branded Lexmark.  What is the actual model number?  I didn't see it in your post, though I might be blind.

---

### Post by jrsc109 on 2008-09-15
It's a Dell 924 (All In One)

---

### Post by Thelasko on 2008-09-15
[OpenPrinting]("http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Photo_924") says it's a "paperweight" on Linux.  Sorry:(

Some printers just use weird drivers.  Most of those printers are manufactured by Lexmark.

---

