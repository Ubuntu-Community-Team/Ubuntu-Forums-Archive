---
title: "[SOLVED] Pre emptive Printer question?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-17
OK I've learnt to configure things such as my wireless card with Ndiswrapper and get it working on my laptop. Ironically when I tried my desktop which uses an external rather unusual card it fired straight up even though the specs make no mention of supporting linux!

So far I've not dared to try printing. I just got a new HP printer and as expected it makes no mention of Linux. So what can I expect? I have the windows drivers, am I going to need something similar to the WiFi card routine? Is there any best and logical order I should approach this when I connect it up? I working from the asumption that its not going to work initially!

---

### Post by Mud.Knee.Havoc on 2008-08-17
HP is pretty good for working under linux.

Check out [this website]("http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro"), which contains a database of printers (including how well they work, and tricks you may need to get them going).

[Here's the HP list]("http://www.openprinting.org/printer_list.cgi?make=HP").

EDIT: I forgot to answer the other half of your question.  Assuming that it's one of the printers in the list that works well, it might be as easy as going to System->Administration->Printing->New Printer (if it sees the printer).  I'm running an HP fax/printer/copier combo and had to install a driver (which is available either from HP's site or via synaptic).  If you mention the model of your printer, we might be able to offer some tips.

You will definitely not need your Windows driver for this.  The wifi drivers are a bit different in this regard.

---

### Post by mariane_08 on 2008-08-17
> **Mud.Knee.Havoc said:**
> HP is pretty good for working under linux.

Check out [this website]("http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro"), which contains a database of printers (including how well they work, and tricks you may need to get them going).

[Here's the HP list]("http://www.openprinting.org/printer_list.cgi?make=HP").

EDIT: I forgot to answer the other half of your question.  Assuming that it's one of the printers in the list that works well, it might be as easy as going to System->Administration->Printing->New Printer (if it sees the printer).  I'm running an HP fax/printer/copier combo and had to install a driver (which is available either from HP's site or via synaptic).  If you mention the model of your printer, we might be able to offer some tips.

You will definitely not need your Windows driver for this.  The wifi drivers are a bit different in this regard.

Thanks! The printer is a very inexpensive HP Deskjet D 1460. I'll be honest I've not really tried yet but will probably have a go later tonight. Just thinking ahead :)

---

### Post by Mud.Knee.Havoc on 2008-08-17
Lucky you!  [It's on the list]("http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460"), and is supposed to work perfectly.  The driver "hplip" referred to is available via synpatic.

---

### Post by mariane_08 on 2008-08-17
Well it almost went perfectly! There's even HPLIP already installed so didn't need to download. I configured under System>Administration>Printing.

The only problem is it prints a blank page! I ran the printing troubleshooter which did not give an answer but the following bug report:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0xfecbf0>,
 'cups_instance': None,
 'cups_queue': 'Deskjet_D1400_series',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/Deskjet_D1400_series?serial=TH7BM3544Z04Y2',
                       'printer-info': u'HP Deskjet D1460',
                       'printer-is-shared': True,
                       'printer-location': u'm2000',
                       'printer-make-and-model': u'HP DeskJet D1400 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Deskjet_D1400_series'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [6],
 'test_page_job_status': [(5, 'Deskjet_D1400_series', 'Test Page'),
                          (6, 'Deskjet_D1400_series', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by mariane_08 on 2008-08-24
OK anyone have any ideas why I'm printing a blank page? I'm connecting to the printer just fine and fast. I click print and it prints straight away...just nothing there! :confused:

---

### Post by public_void on 2008-08-24
I had a similar problem once, however with an old Epson printer. I found using the CUPS web interface much better, then using the Gnome interface (Desktop->Administration->Printing). Try uninstalling the printer. Then using your browser navigate to [http://localhost:631/](http://localhost:631/). From the home tab use the 'Add Printer' button. Set the Name, Location and Description. Next select the device, it should be listed, after this select the driver.

---

### Post by bumanie on 2008-08-24
Go to the hp linux site and download the self-extracting installer. Once installed, everything should work perfectly. The installer asks a few basic questions, takes 20-30 minutes, but, at least for me, has always worked without any problems. I had a similar problem where hplip did not work well when the printer was installed after the OS, but it does 'self-install' well, when the printer is plugged during the OS installation.

---

