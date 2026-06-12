---
title: "Help Sharing a Windows Printer Please"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by efincoop on 2008-09-30
Hello, I am a new Unbuntu (Hardy 8.04.1) user.  I have been scouring this forum and the web to try and get my Ubuntu PC to print to a printer connected to my Windows PC.

I have installed and configured samba to the best of my abilities using this guide [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Using the Printer Configuration Tool I can browse and locate my printer.  I can load the driver, but I can not seem to communicate with the printer using the Verify function with or without the authentication option.

My userid on both machines is the same as is my password.  I ran the Printer Configuration Tool trouble shooting function and got the the following information:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fe6e0>,
 'cups_instance': None,
 'cups_queue': 'PIXMA_iP4500',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://COOPERSTAH/OFFICEPC/CanoniP4500',
                       'printer-info': u'Canon IP4500 on Office PC',
                       'printer-is-shared': True,
                       'printer-location': u'Basement',
                       'printer-make-and-model': u'Canon PIXMA iP4500 - CUPS+Gutenprint v5.0.2 Simplified',
                       'printer-state': 4,
                       'printer-state-message': u'Unable to connect to CIFS host, will retry in 60 seconds...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 176156,
                       'printer-uri-supported': u'ipp://localhost:631/printers/PIXMA_iP4500'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to connect to CIFS host, will retry in 60 seconds...',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(2, 'PIXMA_iP4500', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to connect to CIFS host, will retry in 60 seconds...',
 'printer-state-reasons': 'none'}


Any help would be greatly appreciated.

---

### Post by cariboo on 2008-09-30
You don't need samba to share a computer attached to a windows computer. You really don't need authentication if you aren't going to be setting up print quotas. If your network is behind a router no one will be able to acces your printer except for the cpmputers on your network.

Make sure you windows  computer is sharing the printer. To do this in Windows go to Start-->Printers and Faxes, if you are using XP Pro, Start-->Control Panel-->Printers and Faxes in XP Home, right click on the printer you want to share and click sharing, click the printer sharing radio button and give your printer a name, then click the apply button. You should now be ready to share.  

Jim

---

### Post by efincoop on 2008-09-30
Hmmm... Okay, I have verified that the printer is shared as you describe.  SO I have 2 questions:

Should I be able to send a test page to the printer from the Printer Configuration Function?

Should I uninstall samba?

---

### Post by efincoop on 2008-09-30
I just tried to print an Open Office document... no joy :(

---

### Post by jonandrews on 2008-11-03
I've put a step-by-step guide to printing from Ubuntu to a printer attached to an XP pc on:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

I hope it is helpful.

---

