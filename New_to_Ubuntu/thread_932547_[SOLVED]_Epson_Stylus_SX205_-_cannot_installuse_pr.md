---
title: "[SOLVED] Epson Stylus SX205 - cannot install/use printer and scanner"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by stormtrooprdave on 2008-09-28
I've looked over these forums and found various threads but still cannot use my printer with Ubuntu. I have the Epson Stylus SX205 All In One Printer Scanner & Copier.  

When I run xsane it says no scanner found.  

If I go into system > administration > printing my printer is listed there and I have made it the default printer but still nothing happens when I try to print.  If I do a test page from this screen it says it will be added as a job.  So now I have 5 jobs but I can't figure out how to access the print queue.

I followed the instructions in these threads but still can't get it working

[http://ubuntuforums.org/showthread.php?t=822003&highlight=epson+stylus]("http://ubuntuforums.org/showthread.php?t=822003&highlight=epson+stylus")
[http://ubuntuforums.org/showthread.php?t=903905&highlight=epson+stylus]("http://ubuntuforums.org/showthread.php?t=903905&highlight=epson+stylus")

Please help!!!

---

### Post by stormtrooprdave on 2008-09-30
bump

---

### Post by stormtrooprdave on 2008-10-08
bump

---

### Post by hadimosuur on 2008-10-23
Hello, 

for printing try to choose the driver for dx4800. Ubuntu Hardy Heron offers it.
(System>Administration>Printing(or sth similar)>Settings - change "type and model" (or shape?)
This advice is from here:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2144179#p2144179](http://forum.ubuntu-fr.org/viewtopic.php?pid=2144179#p2144179)

Sorry for my English...

My sx205 is printing with this change :)
Scanning not solved yet...

Bye from Bohemia (CZ)

---

### Post by stormtrooprdave on 2008-10-27
> **hadimosuur said:**
> Hello, 

for printing try to choose the driver for dx4800. Ubuntu Hardy Heron offers it.
(System>Administration>Printing(or sth similar)>Settings - change "type and model" (or shape?)
This advice is from here:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2144179#p2144179](http://forum.ubuntu-fr.org/viewtopic.php?pid=2144179#p2144179)

Sorry for my English...

My sx205 is printing with this change :)
Scanning not solved yet...

Bye from Bohemia (CZ)

Thanks my printer now prints!!  

Still cannot scan though.  If I go to xsane it says no scanner found.

---

### Post by hadimosuur on 2008-10-30
For scanning try this:

On avasys.jp you can find a driver - debian package.

Direct link for download is:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

but may be it won't work well. So you can go there from here:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

You must choose here:
"Epson Stylus NX200/SX200/SX205/TX200/TX203"
and Distribution and Distrib. version - I chose "others"
and your country, connection environment - "print/scan with local printer or scanner"
and Location for the product - I chose "Individuals(Graphic/Image)"

And now you can click on "Next"

and there will be THE .deb package "**iscan_2.12.0-4_i386.deb**" - in the section "Scanner Driver"  :)

So download it and save it!

Now you must go to the command line. Go to the directory where you saved the package to (use the command cd -e.g.: cd /home/MyFolder). And now install the package: write "sudo dpkg --install iscan_2.12.0-4_i386.deb"
put the password

If there will be some failure you must install or uninstall other required packages (use Synaptic) and than try again (sudo dpkg etc.)

When everything is ok you will find Image Scan! in Menu>Applications>Graphics
So start Image Scan!   - and may be it will work!! :)

Good luck!

from Bohemia

---

### Post by stormtrooprdave on 2008-10-30
This is really good news, however there is one last hurdle - I am using 64 bit and it only gives i386 debs!  Can I edit the files inside the deb to make it compatible?

I feel I am so close to getting this working!

---

### Post by hadimosuur on 2008-10-30
Have you installed the package? Doesn't work?
I have got a laptop - Acer Aspire 3690. I think it isn't 386...
But the scanner works:)
So try it...

Bye

---

### Post by stormtrooprdave on 2008-10-30
> **hadimosuur said:**
> Have you installed the package? Doesn't work?
I have got a laptop - Acer Aspire 3690. I think it isn't 386...
But the scanner works:)
So try it...

Bye

I tried it and it wouldn't install as it was the wrong architecture.  You can force 32 bit debs to install on 64bit Ubuntu but it was missing all sorts of dependencies which were not in synaptic.

---

### Post by hadimosuur on 2008-10-30
:( 

"Search" in Synaptic for searching and installing of missing dependencies doesn't work...?

I'm sorry, at the moment I haven't any good advice... - I'm not very experienced...
Perhaps somebody else will help you :cool:

At the avasys website under the links to packages download
there's link to .pdf file - "Installation Method" - it's User's Guide
Perhaps you will find sth useful there...? 

Bye

---

### Post by Melodic_BM on 2008-12-26
Hi,
see [my answer at Launchpad]("https://answers.launchpad.net/ubuntu/+source/system-config-printer/+question/48455") and let me know wether it worked or not ;)

---

### Post by Kaho on 2008-12-31
Hello, 

I've just bought an Epson Stylus SX205.
Printing was quickly made available by using the DX4800 drivers instead but scanning took me some time to work out.

Here is a solution I found on a french website and it worked great !

Open a terminal :
```
lsusb | grep -i epson
```

You should have something similar to this :
```
Bus 001 Device 006: ID 04b8:0849 Seiko Epson Corp.

```

Note the **04b8:0849** numbers, then, 

```
sudo gedit /etc/sane.d/epson.conf
```

Look for the line 
```
# usb 0x??? 0x???
```

Replace them by the numbers you've noted before : **0x48b 0x849**
and **uncomment the line**  ( by removing the # )
[B]
Uncomment also these two lines [/B]:
```
# usb /dev/usbscanner0
# usb /dev/usb/scanner0
```

Then, you will notice that Xsane only recognizes your scanner if you launch it as ROOT, but it is not recommanded.

Instead, just modify **udev rules** :
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
( file may be empty )

And paste this :
```
# Epson Stylus SX205
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0849", MODE="664", GROUP="scanner"
```

Then, restart udev :
```
sudo /etc/init.d/udev restart
```

( You may also need to add yourself in the **scanner group**... see groups and membership options in gnome control center)

And voilà !

Hope it will work for other SX205 users too :D

---

### Post by stormtrooprdave on 2009-01-01
A million thank yous! This worked perfectly!

I used a pizza menu to test out the scanner so now I'll never to hunt round for missing menus when I get the munchies lol

---

### Post by Melodic_BM on 2009-01-01
Can you please try it with the iscan packages I postet in my last post? Would be nice to know if that packages work with sx205 as well :)

---

### Post by stormtrooprdave on 2009-01-01
> **Melodic_BM said:**
> Can you please try it with the iscan packages I postet in my last post? Would be nice to know if that packages work with sx205 as well :)

Those packages are 386 and I have 64 bit so maybe someone else can try them

---

### Post by Kango_V on 2009-01-10
Anyone got ant pointers about getting an Epson PX800FW scanner working?
I've gone through this thread and tried installing iscan doing the changes for UDEV, but still no joy.

xsane runs, but when I click Acquire, it says "Failed to start scanner.  Operation not supported".

iscan says "Could not send command to scanner.  Check the scanners's status."

Not sure what to do now.  And I'm on AMD64.

daz

---

### Post by Smurf1979 on 2009-01-19
Hi

I have followed the instruktions in this thread and i got the printer runing but i can't install the scanner when i trie to install "iscan_2.12.0-4_i386.deb" it opens packe manger but i says "error: dependency is not satisfiable: libltdl3" and i have searched fore libltdl and all there are is libltdl7, what sould i do?

---

### Post by stormtrooprdave on 2009-01-20
All of a sudden I find myself unable to print.  I am getting a message saying Printer 'Stylus-SX2002' may not be connected.

When I look on the cups page on [http://localhost:631/printers/](http://localhost:631/printers/) it says the following:

Stylus-SX2002 "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4b8_849_4B4C4E4B3032393760_if1_printer_noserial": Permission denied"

---

### Post by Kaho on 2009-01-21
Haha, I wanted to print something a week ago and I got this damn " Printer 'Stylus-SX205' may not be connected " too !!

I found it very weird because printing worked fine before and couldn't determine if this problem was due to the scan trick I gave you before ( I don't remember if I tried to print something after these modifications... )

Anyways, I have just found a solution, again, on the [*_french ubuntu forum_*]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2121538#p2121538") :

Apparently, it has something to do with /dev/usb/lp0 being attributed to the 'scanner' group instead of the 'lp' group...

With a simple ```
**sudo chgrp lp /dev/usb/lp0**
```
it returned to normal !
( the tip in the french thread says that this modification works if the printer is connected to the usb lp0 port...and that may be the case in most configurations )

**After that, printing AND scanning with Epson SX205 were available on my Ubuntu Intrepid** !

I came back to this thread because I wanted to ask you if you have faced the same problem... and yes you have !

So, I hope this can help you now ;)




To Smurf1979 : you should follow the instructions in my previous post instead( and it worked for me and stormtrooprdave ! :) )
You know, I tried to install these iscan packages before, but with no success because I got the same dependency error ...





As for the Kango_V's PX800 problem, sorry but I have no clue how to make it work... ( a guy posted something a month before about this on the french ubuntu forum but it is not resolved yet... )

---

### Post by Smurf1979 on 2009-01-22
Yes thank tou it worked I don't know what happedt but the first time i tryed it noting happend when i entered sudo gedit /etc/sane.d/epson.conf but this time it did and now both printer and scanner works. :P:D:cool:

---

### Post by stormtrooprdave on 2009-01-22
> **Kaho said:**
> Haha, I wanted to print something a week ago and I got this damn " Printer 'Stylus-SX205' may not be connected " too !!

I found it very weird because printing worked fine before and couldn't determine if this problem was due to the scan trick I gave you before ( I don't remember if I tried to print something after these modifications... )

Anyways, I have just found a solution, again, on the [*_french ubuntu forum_*]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2121538#p2121538") :

Apparently, it has something to do with /dev/usb/lp0 being attributed to the 'scanner' group instead of the 'lp' group...

With a simple ```
**sudo chgrp lp /dev/usb/lp0**
```
it returned to normal !
( the tip in the french thread says that this modification works if the printer is connected to the usb lp0 port...and that may be the case in most configurations )

**After that, printing AND scanning with Epson SX205 were available on my Ubuntu Intrepid** !

I came back to this thread because I wanted to ask you if you have faced the same problem... and yes you have !

So, I hope this can help you now ;)




To Smurf1979 : you should follow the instructions in my previous post instead( and it worked for me and stormtrooprdave ! :) )
You know, I tried to install these iscan packages before, but with no success because I got the same dependency error ...





As for the Kango_V's PX800 problem, sorry but I have no clue how to make it work... ( a guy posted something a month before about this on the french ubuntu forum but it is not resolved yet... )

Yes Kaho it worked!  Where is the thank you button when you need it! :D

Viva la forum francais lol

---

### Post by Kango_V on 2009-01-31
Very strange all this.  I'll just have to use the PX800FW's ability to scan to a flash card.

Annoying though.

---

### Post by taronski on 2009-02-02
Hiya,

I am painfully new to Linux (ubuntu intrepid)

I followed the instructions in the post but still no luck.

Attached the bug report

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Stylus-SX200 (default)>,
 'cups_instance': None,
 'cups_queue': 'Stylus-SX200',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20SX200',
                       'printer-info': u'EPSON Stylus SX200',
                       'printer-is-shared': True,
                       'printer-location': u'Beast',
                       'printer-make-and-model': u'Epson Stylus Scan 2500 - CUPS+Gutenprint v5.2.0-rc1',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8556556,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus-SX200'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C0L0': {u'StpInkSet': u'None'},
                               u'C0L2': {u'StpPrintingDirection': u'None',
                                         u'StpWeave': u'None'},
                               u'C0L3': {u'StpInkType': u'None'},
                               u'C0L4': {u'StpFeedSequence': u'None'},
                               u'C1L0': {u'StpBrightness': u'None',
                                         u'StpColorCorrection': u'None',
                                         u'StpContrast': u'None',
                                         u'StpFineBrightness': u'None',
                                         u'StpFineContrast': u'None',
                                         u'StpFineSaturation': u'None',
                                         u'StpImageType': u'TextGraphics',
                                         u'StpSaturation': u'None'},
                               u'C1L1': {u'StpBlackDensity': u'None',
                                         u'StpCyanDensity': u'None',
                                         u'StpDensity': u'None',
                                         u'StpDitherAlgorithm': u'None',
                                         u'StpFineBlackDensity': u'None',
                                         u'StpFineCyanDensity': u'None',
                                         u'StpFineDensity': u'None',
                                         u'StpFineMagentaDensity': u'None',
                                         u'StpFineYellowDensity': u'None',
                                         u'StpMagentaDensity': u'None',
                                         u'StpYellowDensity': u'None'},
                               u'C1L2': {u'StpBlackGamma': u'None',
                                         u'StpCyanBalance': u'None',
                                         u'StpCyanGamma': u'None',
                                         u'StpFineBlackGamma': u'None',
                                         u'StpFineCyanBalance': u'None',
                                         u'StpFineCyanGamma': u'None',
                                         u'StpFineGamma': u'None',
                                         u'StpFineMagentaBalance': u'None',
                                         u'StpFineMagentaGamma': u'None',
                                         u'StpFineYellowBalance': u'None',
                                         u'StpFineYellowGamma': u'None',
                                         u'StpGamma': u'None',
                                         u'StpMagentaBalance': u'None',
                                         u'StpMagentaGamma': u'None',
                                         u'StpYellowBalance': u'None',
                                         u'StpYellowGamma': u'None'},
                               u'C1L4': {u'StpLinearContrast': u'False'},
                               u'C1L5': {u'StpBlackTrans': u'None',
                                         u'StpDropSize1': u'None',
                                         u'StpDropSize2': u'None',
                                         u'StpDropSize3': u'None',
                                         u'StpFineBlackTrans': u'None',
                                         u'StpFineDropSize1': u'None',
                                         u'StpFineDropSize2': u'None',
                                         u'StpFineDropSize3': u'None',
                                         u'StpFineGCRLower': u'None',
                                         u'StpFineGCRUpper': u'None',
                                         u'StpFineInkLimit': u'None',
                                         u'StpGCRLower': u'None',
                                         u'StpGCRUpper': u'None',
                                         u'StpInkLimit': u'None'},
                               u'General': {u'ColorModel': u'RGB',
                                            u'MediaType': u'Plain',
                                            u'OutputOrder': u'Reverse',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'361x360dpi',
                                            u'StpColorPrecision': u'Normal',
                                            u'StpQuality': u'Standard',
                                            u'StpiShrinkOutput': u'Shrink'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:Stylus SX200;CLS:PRINTER;DES:EPSON Stylus SX200;',
                      'device-info': u'EPSON Stylus SX200 USB #1',
                      'device-make-and-model': u'EPSON Stylus SX200'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 5028L}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [8],
 'test_page_job_status': [(False,
                           7,
                           'Stylus-SX200',
                           'Printer Maintenance',
                           'Stopped',
                           None),
                          (True,
                           8,
                           'Stylus-SX200',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 8,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/8',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'taron',
                            'job-printer-state-message': u'Printing page 1, 21%',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1233580966,
                            'job-printer-uri': u'ipp://Beast:631/printers/Stylus-SX200',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/8',
                            'job-uuid': u'urn:uuid:4ec02214-0016-3e6f-44c6-2267243a0c95',
                            'printer-uri': u'ipp://localhost/printers/Stylus-SX200',
                            'time-at-completed': None,
                            'time-at-creation': 1233580960,
                            'time-at-processing': 1233580960})],
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['I [02/Feb/2009:13:22:34 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Adding start banner page "none".',
               'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Adding end banner page "none".',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] File of type application/postscript queued by "taron".',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Queued on "Stylus-SX200" by "taron".',
               'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pstopdf (PID 10218)',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pdftopdf (PID 10221)',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pdftoraster (PID 10224)',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/rastertogutenprint.5.2 (PID 10226)',
               'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started backend /usr/lib/cups/backend/usb (PID 10228)',
               'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:43 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:43 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:46 +0000] Saving subscriptions.conf...',
               'I [02/Feb/2009:13:22:46 +0000] Saving subscriptions.conf...']}
Page 11 (Printer state reasons):
{'printer-state-message': u'Printing page 1, 21%',
 'printer-state-reasons': [u'none']}

---

### Post by stormtrooprdave on 2009-02-19
> **Kaho said:**
> Apparently, it has something to do with /dev/usb/lp0 being attributed to the 'scanner' group instead of the 'lp' group...

With a simple ```
**sudo chgrp lp /dev/usb/lp0**
```
it returned to normal !


Back again!  I don't print that often but I find I am having to enter that code after every restart when I want to print.  Why won't it stick between reboots?

---

### Post by Kaho on 2009-02-26
Well, sorry but this time I have no solution... :( 

It realized every time I plug in my printer, I have to enter these lines, so I just created an alias for this command which is easier to remember...
( and truth is that my Epson SX205 is now connected to my AOLbox for printing share so I only have to plug in to my laptop when I need to scan something... xD )

As for Taronski, as I have no clue what these errors mean( I'm actually kinda newbie to Ubuntu too xD )  if my instructions didn't work, maybe you should try the iscan packages mentionned before...
( [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) )

Following this french thread :
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2367824#p2367824](http://forum.ubuntu-fr.org/viewtopic.php?pid=2367824#p2367824) it seems to work...
And a link to the missing library is even provided ( but for Hardy... )
And if someone doesn't understand what it is said, I can translate it :) 

Good luck !

---

### Post by julian.coccia on 2009-03-04
> **Kango_V said:**
> Anyone got ant pointers about getting an Epson PX800FW scanner working?
I've gone through this thread and tried installing iscan doing the changes for UDEV, but still no joy.

xsane runs, but when I click Acquire, it says "Failed to start scanner.  Operation not supported".

iscan says "Could not send command to scanner.  Check the scanners's status."

Not sure what to do now.  And I'm on AMD64.

daz

It might be a permission problem. Try this: sudo iscan

Also, if you hit a dpi limit, check this thread:
[http://ubuntuforums.org/showthread.php?t=1086953](http://ubuntuforums.org/showthread.php?t=1086953)

---

### Post by Nick Hill on 2009-07-02
> **Kaho said:**
> Hello, 

I've just bought an Epson Stylus SX205.
Printing was quickly made available by using the DX4800 drivers instead but scanning took me some time to work out.

Here is a solution I found on a french website and it worked great !
...

I think this needs to be addressed in the sane-backends, so that other user's don't need to configure sane manually.

I have raised a bug:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/394528](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/394528)

---

### Post by jamesgthang on 2009-11-23
Thanks... Kaho.  Great instuctions.   I am using an Epson Stylus TX200 on Ubuntu 9.10 and it worked like a charm. 

Some differences:  My sane was configured to use /etc/sane.d/epson2.conf and not /etc/sane.d/epson.conf.  So I changed the epson2.conf file instead.  

Thanks again.

---

### Post by howlep on 2009-12-21
i also had to use the epson2.conf file. just hope that this helps someone.

---

### Post by Kabezon on 2010-01-18
I got the scanner to work, but only as root, which is useless... I modified the udev rules as stated, but it still won't let scan unless I'm root :S I think the problem is the scanner group, which doesn't appear in the group list.

Sorry to bring a solved thread back to life, I just thought it might be better than creating a new one.

---

### Post by rizitis on 2010-01-27
> **Kaho said:**
> Hello, 

I've just bought an Epson Stylus SX205.
Printing was quickly made available by using the DX4800 drivers instead but scanning took me some time to work out.

Here is a solution I found on a french website and it worked great !

Open a terminal :
```
lsusb | grep -i epson
```

You should have something similar to this :
```
Bus 001 Device 006: ID 04b8:0849 Seiko Epson Corp.

```

Note the **04b8:0849** numbers, then, 

```
sudo gedit /etc/sane.d/epson.conf
```

Look for the line 
```
# usb 0x??? 0x???
```

Replace them by the numbers you've noted before : **0x48b 0x849**
and **uncomment the line**  ( by removing the # )
[B]
Uncomment also these two lines [/B]:
```
# usb /dev/usbscanner0
# usb /dev/usb/scanner0
```

Then, you will notice that Xsane only recognizes your scanner if you launch it as ROOT, but it is not recommanded.

Instead, just modify **udev rules** :
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
( file may be empty )

And paste this :
```
# Epson Stylus SX205
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0849", MODE="664", GROUP="scanner"
```

Then, restart udev :
```
sudo /etc/init.d/udev restart
```

( You may also need to add yourself in the **scanner group**... see groups and membership options in gnome control center)

And voilà !

Hope it will work for other SX205 users too :D

I did it but does not work for me in my 9.10 system
So if someone have the same problem here is what I did:
I install from synaptic libsane extras
Dint work again
After that I did ```
sudo gedit /etc/sane.d/epson2.conf
```
and I change the file like this```
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
usb 0x4b8 0x849  <---- here 
```
At list I can run xsane as root now 
I have an epson SX205

---

### Post by rizitis on 2010-01-27
just run xsane successfully as user (no sudo)
well ```
sudo gedit /lib/udev/rules.d/40-libsane.rules
``` 
and add at the file:```
# Epson SX-205
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0849", ENV{libsane_matched}="yes"
```

restart SX205 



now you can run xsane as user, maybe when click to shutdown  xsane a message window open about permissions but I click close 2 times, however.

---

### Post by Kaho on 2010-08-04
Thanks a lot rizitis for your tip about udev !!
I just upgraded to Lucid and found my scanner didn't work anymore with the line I gave earlier in this thread for libsane rules...

Now, with Ubuntu 10.04, Espon Stylus SX205 works out of the box with its driver and scanner is also ok with these modifications :)

---

