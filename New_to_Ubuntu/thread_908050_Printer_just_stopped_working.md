---
title: "Printer just stopped working"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by snakra on 2008-09-02
Hello,

Help!

I've had my Brother dcp 310cn working fine for the last year and now it's just stopped. Sending a document for print gets a message that data being received but nothing happens.

I did a test print and this is fine.

I got an error message once that there was a CUPS Server error - service unavailable. This error did not appear again!

I'm not on a network/server just a stand alone Acer laptop.  The only thing I've changed recently was to install a wireless router but I've reverted back to the cable as the wireless gave me headaches. Will this have caused a problem.

All help most welcome.

Thanks

SN

---

### Post by Dedoimedo on 2008-09-02
Hello,

CUPS is the printing service, so it seems we're on the right track.

1. Open terminal.
2. Type: sudo /etc/init.d/cupsys restart. << This will restart the printing service.
3. Try printing again, see what happens.

Other basic troubleshooting solutions: turn the printer off/on, restart the machine.

Can you remember what happened when you received the cups error.

Dedoimedo

---

### Post by snakra on 2008-09-02
Hello,

Thank you for your reply.

1 Did as you suggested, 'restarted' Cups - no joy

2 Shut down system and printer and restarted - no joy

3 Sorry, I thought I had just tried to prin when the error message appeared. This does not happen now.  I just get the light coming on in the small display on the printer which says data received but then it goes off without anything being printed.

Is it worth downloading the drivers again?

Help

SN

---

### Post by Dedoimedo on 2008-09-02
Hello,
Do you know what you did before this problem started?
Can you trace back to the root cause, perhaps?
Dedoimedo

---

### Post by snakra on 2008-09-02
Hello,

Sorry, I really don't know what I did to cause the problem.

I've downloaded both the printer driver and the CUPS driver and re-installed them.

I deleted the installed printer and then re-installed it.

Still no joy.

I tried the troubleshooting process which said it could not help but provided the following:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8d11320>,
 'cups_instance': None,
 'cups_queue': 'DCP-310CN',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/DCP-310CN',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'sheri-laptop',
                       'printer-make-and-model': u'Brother DCP-310CN CUPS v1.1',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135244,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DCP-310CN'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [], 'test_page_successful': True}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

Getting the printer to work had been the hardest bit when I moved to Ubuntu and I had been pleased to get it to work but this episode has really got me down.

Help!!

SN

---

### Post by plucky on 2008-09-02
This is just a thought,check the default paper size that is set for the printer.Make sure it is A4 and not letter.

Also try using the cups interface to check the error log.In Firefox address bar input ```
localhost:631/admin/
``` will open the CUPS interface.Search for the errorlog and see if there is anything obvious.


Good Luck

---

### Post by snakra on 2008-09-03
Hello to both Dedoimedo and Plucky for your interest and help.

First, the important thing for me is that the printer is back in action.

For others, the even more important thing is did one learn anything from this episode?

Yesterday, I had downloaded and re-installed afresh the printer and cups drivers and had no joy and gave up. Today I restarted the machine and guess what - it all worked. I can only think that the machine needed a reboot after the re-installation of the drivers - stupid of me.

Yes, the printer was set to 'letter' rather than A4 but that did not affect the outcome. I've changed the setting to A4.

I did get the Error log as you suggested and I copy that below for anybody who is interested - doesn't make much sense to me except that some authorizations were missing! 

You may also find it interesting that when I updated from 7.10 to 8.04 I lost the printer sand had to re-install the drivers - and,yes I had to re-boot!

The error log:

E [02/Sep/2008:09:24:17 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:09:25:14 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Sep/2008:09:25:25 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:09:26:07 +0100] CUPS-Set-Default: Unauthorized
E [02/Sep/2008:09:26:30 +0100] CUPS-Set-Default: Unauthorized
E [02/Sep/2008:09:28:05 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:28:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:28:56 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:29:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:09:31:56 +0100] Pause-Printer: Unauthorized
E [02/Sep/2008:16:25:26 +0100] Resume-Printer: Unauthorized
E [02/Sep/2008:18:26:42 +0100] Filter "brlpdwrapperDCP310CN" for printer "DCP-310CN" not available: No such file or directory
E [02/Sep/2008:18:26:49 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Sep/2008:18:28:03 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:29:14 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Sep/2008:18:30:45 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:31:31 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:32:11 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:32:15 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:32:36 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Sep/2008:18:40:53 +0100] Filter "brlpdwrapperDCP310CN" for printer "DCP-310CN" not available: No such file or directory
E [02/Sep/2008:18:41:00 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Sep/2008:18:42:31 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Sep/2008:18:43:32 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Sep/2008:18:43:38 +0100] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [02/Sep/2008:18:58:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:18:58:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:18:58:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:18:58:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Sep/2008:19:03:01 +0100] Pause-Printer: Unauthorized
E [03/Sep/2008:12:37:11 +0100] Resume-Printer: Unauthorized
E [03/Sep/2008:13:01:19 +0100] CUPS-Add-Modify-Printer: Unauthorized

I haven't a clue as to what upset the system.  Could it possibly have been any of the system updates - which I always carry out when the system tells me that updates are available.

Hope this is of use.

Thanks again

SN

---

### Post by Dedoimedo on 2008-09-03
Hello,
After reading around a little, this seems to be a known bug.
I'll check around some more, will get back to you. It's good to hear everything works.
Dedoimedo

---

### Post by tdmoore on 2008-09-03
After working on my issue and looking in the forums, I have a similar issue with a twist.

Running 8.10. Printer is a Xerox Phaser 6110 that used to run perfectly.

Print tests run fine, printing out of Open Office Writer works fine, printing a web page works fine, however in OOo Calc, file does not print!
Have used info posted here to assist me but still not working, yet just over a week ago it did.  I have not done anything except accept the usual Ubuntu updates.

CUPS
Description: Phaser_6110
Location: tim-desktop
Printer Driver: Xerox Phaser 6110 Foomatic/foo2qpdl (recommended)
Printer State: idle, accepting jobs, published.
Device URI: usb://Xerox/Phaser%206110 

Any help would be greatly appreciated as I need this working to do my job.  Thank you.

---

### Post by tdmoore on 2008-09-04
After fiddling around for some time, I finally just copied the sheets into another file thinking I may have had a corrupt file...voila, it worked.

Just advising for others....

---

