---
title: "[SOLVED] Ubuntu 8.04 / HP Deskjet 842c gibberish problem?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by thane1 on 2008-08-13
My Hewlett Packard 842c worked beautifully on the last 3 or 4 versions of Ubuntu with cupsys drivers.  However with the new installation of 8.04 the output is at present now trashed - just gibberish characters - pretty much one line per page (which go on and on).  8.04 lists my printer info as hp:/usb/Deskjet_840C?serial=MX0731W03ZLB.  I subsequently checked my old instl'n of 7.10 and the printservices are listed as cupsys and the associated settings are listed as -1, 19, 19, 19, 19, 19, -1 for 0 through 6.  Cannot seem to find any comparable printservices or settings info in 8.04 though.  Printing a test page via System/Administration/Printing/PrintTestPage just places me back in the same loop of one line gibberish pages.  Also there doesn't seem to be any facility to cancel the printer output and get out of the extended loop.  Got into the 8.04 troubleshooting feature and got the following output:
[COLOR="DarkRed"][I]
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x1000970>,
 'cups_instance': None,
 'cups_queue': 'DESKJET_840C',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_840C?serial=MX0731W03ZLB',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 840C',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP DeskJet 842C Foomatic/cdj550',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET_840C'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [], 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}[/I][/COLOR]

Any ideas?  Have been extremely pleased with HP printers in Ubuntu, except for this one problem.  TIA and cheers.

---

### Post by bmac on 2008-08-13
Try installing the HP print driver HPLIP from the enclosed site. It solved numerous problems with my HP printer. I checked and yours is supported.....

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)


Hope this helps......

---

### Post by thane1 on 2008-08-14
Bmac;
     Many thanks.  Tried your link and had some success.  Got a legible printout, but unfortunately it was about 1.25" wide by 2.5" high.  The next time I tried, I was back to the gibberish characters.  So I tried using an HP 840c setting, which I remembered was the setting my 842c used to run in on previous Ubuntu editions.  Now all is well.  Many thanks Bmac (and many thanks to HP for supporting linux - although the 840c vs 842c problem has been confusing at times).  :)

---

