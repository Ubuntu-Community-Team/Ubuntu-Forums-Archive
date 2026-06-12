---
title: "EPSON Stylus DX5050"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-09-30
I have EPSON Stylus DX5050 which I cannot print with. It used to be connected to a different computer running ubuntu 7.10 and there was no problem.

When I connect it to the computer I automaticly get EPSON Stylus DX5000 (Device URI: usb://EPSON/Stylus%20DX5000).

Make and model: Epson Stylus DX4800 - CUPS+Gutenprint v5.0.2 Simplified



I found that the linux driver for DX4800 works alright for my printer (DX5050) so everything should be fine. But it isn't. When I try to print it just says "Processing" and never finish processing no matter for how long I wait.

Now it says "Printer Stylus_DX5000 may not be connected". When I cancel the test the printer goes into "idle" state according to the print program (System &#8594; Administration &#8594; Printer) and when trying to print another test print it doesnt go through the processing stage.

I have changed between 2 usb ports, but have 3 others.

Any ideas?

---

### Post by Bölvaður on 2008-09-30
```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x901ac20>,
 'cups_instance': None,
 'cups_queue': 'Stylus_DX5000',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20DX5050',
                       'printer-info': u'EPSON Stylus DX5050',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus DX4800 - CUPS+Gutenprint v5.0.2',
                       'printer-state': 3,
                       'printer-state-message': u'Printer busy; will retry in 5 seconds...',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 8556556,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_DX5000'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Printer busy; will retry in 5 seconds...',
 'printer-state-reasons': 'connecting-to-device'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(28, u'Job canceled.')],
 'test_page_job_id': [28, 29],
 'test_page_job_status': [(28, 'Stylus_DX5000', 'Test Page'),
                          (29, 'Stylus_DX5000', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Gutenprint Printing page 1, 57%',
 'printer-state-reasons': 'connecting-to-device'}

```

---

### Post by aggelos_930 on 2008-12-15
i have the same problem please help

---

### Post by Neva on 2012-04-28
I got a Epson Stylus DX5050 inkjet multifunction printer/scanner to work in Ubuntu Lucid Lynx 10.04 by using this driver:

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

There's a good manual related to the download, but in short:

[LIST=1]
[*]go to your CUPS administration [http://localhost:631/](http://localhost:631/) and delete any printer drivers you currently have installed
[*]Install Linux Standard Base support from the terminal with the command: **sudo apt-get install lsb**
[*]Download the appropriate installer package from the avasys site. Mine was epson-inkjet-printer-escpr_1.1.1-1lsb3.2_i386.deb
[*]Install the downloaded package
[*]Restart your cups server from the command line: sudo /etc/init.d/cups restart
[*]Plug the printer in to your USB port. The driver DX5000 should install automatically. If not, you can do it from the CUPS browser interface by following the manual provided on the avasys site.
[/LIST]
Hope it works for you as well!

---

### Post by barrytesta on 2012-04-28
> **Neva said:**
> I got a Epson Stylus DX5050 inkjet multifunction printer/scanner to work in Ubuntu Lucid Lynx 10.04 by using this driver:

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

There's a good manual related to the download, but in short:

[LIST=1]
[*]go to your CUPS administration [http://localhost:631/](http://localhost:631/) and delete any printer drivers you currently have installed
[*]Install Linux Standard Base support from the terminal with the command: **sudo apt-get install lsb**
[*]Download the appropriate installer package from the avasys site. Mine was epson-inkjet-printer-escpr_1.1.1-1lsb3.2_i386.deb
[*]Install the downloaded package
[*]Restart your cups server from the command line: sudo /etc/init.d/cups restart
[*]Plug the printer in to your USB port. The driver DX5000 should install automatically. If not, you can do it from the CUPS browser interface by following the manual provided on the avasys site.
[/LIST]
Hope it works for you as well!
I had a printer problem also. When I downloaded the drivers from avasys for one of the files it asked to open with installer. I chose that option and it did an automatic install.
unbuntu 12.0r LTS
good luck

---

