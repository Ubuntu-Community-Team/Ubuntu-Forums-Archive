---
title: "Using Canon i350"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by FrancesL on 2008-08-11
Has anyone go any suggestions on how to use Canon i350 printer with Hardy, Please?

---

### Post by eightmillion on 2008-08-11
That printer purportedly works with [turboprint.]("http://freshmeat.net/projects/turboprint/")

---

### Post by FrancesL on 2008-08-11
> **eightmillion said:**
> That printer purportedly works with [turboprint.]("http://freshmeat.net/projects/turboprint/")

Thanks for that, but not prepared to spend $30 for it.

---

### Post by eightmillion on 2008-08-11
[This page]("http://www.linuxquestions.org/hcl/showproduct.php?product=2172&cat=myprod") seems to suggest that it also works with the s200 drivers. Have a look [here.]("http://gimp-print.sourceforge.net/")

---

### Post by ramjet_1953 on 2008-08-11
Here's what the Open Printing Database has to say:

[http://openprinting.org/show_printer.cgi?recnum=Canon-i350](http://openprinting.org/show_printer.cgi?recnum=Canon-i350)

Regards,
Roger :cool:

---

### Post by FrancesL on 2008-08-23
Tried to install as per info found.
but this is what the trouble shooter says:
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x9ce1420>,
 'cups_instance': None,
 'cups_queue': 'i350',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/i350',
                       'printer-info': u'',
                       'printer-is-shared': False,
                       'printer-location': u'frances-laptop',
                       'printer-make-and-model': u'Canon S200 - CUPS+Gutenprint v5.0.2 Simplified',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2265100,
                       'printer-uri-supported': u'ipp://localhost:631/printers/i350'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(42, u'Job completed.')],
 'test_page_job_id': [42],
 'test_page_job_status': [(42, 'i350', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}



Thus I am still unable to use it

---

### Post by kloper on 2009-05-10
Has anyone any idea how to make the Canon i350 work with Ubuntu? Then please tell us. ;)

I have tried all the Sxxx Gutenprint drivers (e.g. Canon S200 - CUPS+Gutenprint v5.2.3), since some people have managed to get their i450 and i550 printers working with those drivers. No success for me, though.

Seems a bit harsh to cough up $30 for a [commercial driver]("http://www.turboprint.info/").

---

### Post by Didius Falco on 2009-05-10
I did a little Googling on it - unfortunately, the Ubuntu Hardware Compatibility List says it is crap...

I did find this - it's a blog post that is a bit old, and it's definitely not the most elegant solution, but I'll leave it up to you to decide if it's worth a try:

[http://blog.hidari.lt/vmware-ubuntu-710/](http://blog.hidari.lt/vmware-ubuntu-710/)

I hope it helps...

Regards,

Didius

---

