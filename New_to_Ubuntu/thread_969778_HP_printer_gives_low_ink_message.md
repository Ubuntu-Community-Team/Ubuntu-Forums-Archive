---
title: "HP printer gives low ink message"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by tombo465 on 2008-11-03
I use an HP 1300 series all in one with Ubuntu 8.04. It was working fine aside from the low ink messages, but all of a sudden it's not working.A program came up to help diagnose the problem it printed the test page fine , but then said to report the problem as a bug and gave the following out put to include in the bug report.(I don't know how to submit a bug report).file:///home/tberry/printer_bug_report

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8f5b3e0>,
 'cups_instance': None,
 'cups_queue': 'psc_1300_series',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/psc_1300_series?serial=MY3A1BD2T69F',
                       'printer-info': u'hp psc 1300 series',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP PSC 1300 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'marker-supply-low-warning'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/psc_1300_series'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': 'marker-supply-low-warning'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(33, u'Job completed.')],
 'test_page_job_id': [33],
 'test_page_job_status': [(29, 'psc_1300_series', ''),
                          (30, 'psc_1300_series', ''),
                          (33, 'psc_1300_series', 'Test Page')],
 'test_page_successful': True}
Page 5 (Printer state reasons):
{'printer-state-message': '',
 'printer-state-reasons': 'marker-supply-low-warning'}
Please help. Thank you!

---

### Post by cmnorton on 2008-11-07
You submit a bug report by creating an account in Ubuntu Launchpad.

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

It probably would not hurt to contact HP and/or look out on the internet for an updated driver.

---

### Post by mwm1998 on 2009-04-01
This is not an HP issue.  The low ink warning does comes from the HP printer.  I've seen several threads about this with no solution concerning several printers (mostly HP).  The problem is how Ubuntu interprets the low ink warning.  Apparently what is happening is that when a multiple page document or multiple documents are in the que, Ubuntu sees the low ink warning and assumes there is not enough ink to finish the job.  One or two pages will print and then everything locks up.  The printer says printing but it is not. The printer finally goes in standby, usually with a partially printed page in progress.  Ubuntu is still showing everything in the print que.  When unsing Windows OS this problem never occurs. In windows you get low ink warning on Printer and from hp software but printing is not interfered with.  You can print until print quality degrades.  Help please, this is my most serious issue.  HP cartridge are know to give low ink warning well before quality degrades.  HP says it because the want to insure print quality.  Methinks HP wants to sell more ink cartridges.

---

### Post by wolfen69 on 2009-04-01
there's a great HP utility called HPLIP Toolbox. it will tell you ink levels, allow you to clean ink jets, and other advanced options. check it out.
```
sudo apt-get install hplip-gui
```
it will show up in system>preferences.

---

### Post by lndeveloper on 2011-04-09
> **mwm1998 said:**
> This is not an HP issue.  The low ink warning does comes from the HP printer.  I've seen several threads about this with no solution concerning several printers (mostly HP).  The problem is how Ubuntu interprets the low ink warning.  Apparently what is happening is that when a multiple page document or multiple documents are in the que, Ubuntu sees the low ink warning and assumes there is not enough ink to finish the job.  One or two pages will print and then everything locks up.  The printer says printing but it is not. The printer finally goes in standby, usually with a partially printed page in progress.  Ubuntu is still showing everything in the print que.  When unsing Windows OS this problem never occurs. In windows you get low ink warning on Printer and from hp software but printing is not interfered with.  You can print until print quality degrades.  Help please, this is my most serious issue.  HP cartridge are know to give low ink warning well before quality degrades.  HP says it because the want to insure print quality.  Methinks HP wants to sell more ink cartridges.


I have the same problem with my HP D2660 Printer with refilled ink cartridges. I receive a low ink warning and printer does not work at all. I use Ubuntu 11.04. I also believe that it is a fake problem, as the printer works perfect under Windows XP. 

After 2 years of the original post, has anyone found a solution. I think it is somewhat ridiculous to have our printers locked under linux and free to print under windows, don't you think? 

It seems that either we should make linux driver ignore the warning and go on printing, or find a way to reset the printer and (a hardware way) stop that annoying waring from being thrown at all.

---

### Post by s1baker on 2011-04-10
I bought a HP7000 printer, specifically because it could print 13x19 prints and I wanted it primarily as a back-up to my larger 24x36 printer in case it ever went down on me. After setting up the printer and using it a little bit, it sat for about a month and when I went to use it again, all of the ink was gone. Still haven't figured out where the ink went.

 So I bought some new ink cartridges and after using the machine a little bit, I turned it completely off, unplugged. ( I thought the ink going dry may have been caused because of periodic auto cleaning so I unplugged it. ) After a few weeks I went to use the machine again, and 2 cartridges were empty and 2 were full, but I was getting an empty reading on one that was full plus one of the others. Guess they had siphoned out the bottom of the sponge at the bottom of the ink cartridge.  Don't know why the full one was indicating empty.

 I just bout a new printer, because I needed one that had a scanner with it, but it wasn't a HP because of this problem. I think some of the HP printers that have come out lately have a problem with their ink cartridges.

---

### Post by rburkartjo on 2011-04-10
wolf yes that is a great program just installed tks

---

### Post by glentrobfc on 2011-05-11
The gui is nice.  However, it is not intuitively obvious how to kill the offending low on ink issue.  This issue essentially makes the printer unusable.  

I have a Photosmart C4680 and with a black XL cartridge, when the warning first comes up, I still have at least another 100 pages of good printing left.  The printer is on my desktop machine running Ubuntu 10.10.  I have a netbook running either Mint 10, Mint 11 RC, or Ubuntu 11.04.  From my netbook, I do a lot of work (wireless) using Qtnx to the desktop.  I launch several print commands while working on various things and eventually go downstairs to get the prints.  Alas, there are no prints because they are all stuck in the queue because of the low ink warning.

:( A plea, can anybody tweak cups so that we can tell it to ignore HP's Low on Ink warnings.  If somebody could make such a tweak the printer might become usable for myself and others with similar configurations.

---

### Post by chepprey on 2011-05-12
I'm having the same problem with a HP Photosmart c4780 All-in-One, Ubuntu 10.10.

Printing a grayscale document doesn't work, the job just hangs in the print queue with a notice saying "pending - low ink".

I can go to the printer's web interface, and it clearly shows the black ink is nearly 50%.  The color levels are low, but I'm only trying to print grayscale.

The Page Setup settings are truly set for grayscale & not color.

I can make grayscale copies directly on the printer just fine, so I'm sure the issue is somewhere in Ubuntu land.

---

### Post by Timbo24 on 2011-06-02
I have the same false low ink message problem with an HP7000.  My temporary fix is to un-install the printer then reinstall.

S1baker, I don't lose ink, the printer works well for me.

---

### Post by DawieS on 2011-06-07
A few years ago, I bought one of these HP 4-in-1 printer/fax combo's. It printed excellent, however the ink cartridges amounted to a small fortune, especially when the children had to print their many school assignments.

I then started refilling the cartridges, but was less successful at first. After a lot of searching for solutions on the Internet, I found out that most (if not all) HP printers stores the unique ID of each cartridge, along with the ink counter (based on number of pages), in memory.

If you refill a previous empty cartridge, the printer blankly refuses to print, and reports the cartridge as empty. Most of the time, "empty" cartridges have more than 30% of the original ink volume still left, but not available for printing.

I then found the following resetting procedure somewhere on the Internet, that I used with great success, until the printer finally got fried as a result of lightning hitting a telephone line nearby:

To reset models:
HP OfficeJet D series  
HP OfficeJet G series (Except model G55)  
HP OfficeJet K series  
HP OfficeJet V series  
HP OfficeJet 4100 series  
HP OfficeJet 4200 series  
HP OfficeJet 5100 series  
HP OfficeJet 5500 series  
HP OfficeJet 5600 series  
HP OfficeJet 6100 series  
HP OfficeJet 6200 series  
HP OfficeJet 7100 series  
HP OfficeJet 7200 series  
HP OfficeJet 7300 series  
HP OfficeJet 7400 series  
HP PSC 900 series  
HP PSC 2200 series  
HP PSC 2400 series  
HP PSC 2500 series  
HP Fax 1240  
HP Photosmart 2500 series  
HP Photosmart 2600 series  
HP Photosmart 2700 series  
 
Press and hold "#" and "9" keys, then turn the printer power on.  
Note: For models that are not fax press the "+" key instead of "#". 

 
To reset models: 
HP PSC 1200 series  
HP PSC 1300 series  
 
Connect and disconnect the power cord from the wall. When the LED's start flashing, press and hold the keys "ON / RESUME" and "Paper Size". When only the LED "ON / RESUME" is flashing, release both keys. When all LED's stop flashing the RESET has been completed.  


To reset models: 
HP Color Copier 180, 190, 280 and 290  
HP OfficeJet G55 and G55xi  
 
Connect the equipment to the power with the keys "-" and "3" pressed.  


To reset models: 
HP 310 Digital Copier  
HP PSC 700 series  
HP PSC 2110 series  
HP PSC 2170 series  
 
Connect the equipment to the power with the keys "Cancel" and "Arrow left" pressed.  


To reset models: 
HP OfficeJet T series  
 
Connect the equipment to the power with the keys "*" and "8" pressed.  


To reset models: 
HP OfficeJet 500 Series  
HP OfficeJet 600 series  
HP OfficeJet 700 series  
 
Connect the equipment to the power with the keys "2" and "3" pressed.  


To reset models: 
HP OfficeJet (model C2890A)  
HP OfficeJet LX  
HP OfficeJet 300 series  
 
Connect the equipment to the power with the keys "*" and "4" pressed.  


To reset models: 
HP Digital Copier Printer 610  
 
Connect the equipment to the power with the keys "+" and "3" pressed.

Note:
After the reset, the equipment memory will be in the "as new" state, and you must re-enter all your default settings such as date, time etc.
:smile::grin::smile:

---

### Post by AlwaysLearning on 2011-12-03
I'm having similar issues here with a HP Photosmart C7280 to which we print from Windows and Linux computers over the Wi-Fi network.

As soon as there's a low-ink warning on one of the cartridges CUPS on all of the Linux computers will refuse to print to it because of the "marker-supply-low-warning" status being returned from the printer driver.

I've tried wolfen69's suggestion of installing hplip-gui but that doesn't provide any way of overriding or ignoring the warning.

I've tried DawieS' suggestion of powering-on the printer while #-9'ing it, but the C7280 must be a bit smarter because it reasserts the warning before a print job has a chance of getting through.

I feel like saying to the hplip driver, "it's a warning, already, get over it!"

There's still several days' worth of printing before the cartridge actually needs to be replaced and the Windows computers are still quite happy to print to it (they just nag you with a message bubble on the desktop after the print job's done). So, for now, the only work around for the Linux computers is to print to PDF then ship the PDF to a Windows computer over the network or a USB key and print it from there.

---

### Post by AlwaysLearning on 2011-12-09
I thought I'd share a way I've just found around this issue. It would seem that CUPS itself adds printers differently to how the HPLIP drivers do it. i.e.: System/Administration/Printing/Server/New/Printer versus hp-setup.

I found that if I deleted the C7280 printer from the Printing panel and installed it from hp-setup (open a Terminal, run hp-setup) then the resulting printer installation completely ignores the marker levels.

So: ignores marker levels and can't display it on computer (bad), but will still print when marker levels are low (good).

Hope this helps.

---

### Post by azabecki on 2012-02-18
@AlwaysLearning:

Thank you very much! I was ready to throw this HP out! (Being an ex-certified HP printer tech thats hilarious). I could not find the option to ignore low ink/toner messages in CUPS anywhere! (and I still can't) but you are correct, by removing the printer from CUPS and using the hp-setup (in the HPLIP package) it does indeed print correctly. The low ink message still comes up, but now it prints!

This was a huge issue for me since I had just gone out and purchased a complete set of after market replacement ink for my HP710Ez (6500a) printer. On top of that, my daughter had a report due and we couldn't print! I had to bust out the portable printer (again, complete comedy at my house because of what I do for a living)

We had a similar issue at the office with an HP color LaserJet, however, everyone in the office but me runs either Mac or Windows, and those drivers do indeed have the option in them to ignore low ink.

So anyways, a long-winded THANK YOU! (and an 'I shoulda thought of that myself') haha You made my day sir.

-Allan

---

