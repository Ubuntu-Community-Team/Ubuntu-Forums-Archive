---
title: "[SOLVED] Please help with HP printer"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-06-25
I have a HP p1005 printer that was working and now has decided to call quits. It is connected to an Acer Aspire 9300 w/ nVidea GeForce 6600. I followed all the setup steps to download the driver at [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) but still cannot print.  The documents just stay in the queue and either say busy or processing.  What are my next steps? 

Also when i plug in the USB cord my computer says "No devices found" even though the driver is installed.

Thank You

---

### Post by drs305 on 2008-06-25
If you go to System, Admin, Printer, does the address look something like this:
```
usb://HP/LaserJet%201000
```

If it has "serial" somewhere in the address correct it.

When you say "no devices found" is that the result of:
```
lsusb
```

---

### Post by FAMUgolfer on 2008-06-25
This is wierd but I just solved my problem.

All I did was system>admin>printing>new printer........and just went from there and now everything is working just fine.

Thank you for your quick response and i will use your advice if this problem arises again.

---

### Post by HJR on 2008-09-10
> **drs305 said:**
> If you go to System, Admin, Printer, does the address look something like this:
```
usb://HP/LaserJet%201000
```

If it has "serial" somewhere in the address correct it.

When you say "no devices found" is that the result of:
```
lsusb
```
Hi, I too am a Linux newbie fighting with the HP P1005.  My address says "serial".  You say to correct it.  How do I do this?  What do I have to replace "serial" with?

---

### Post by drs305 on 2008-09-10
> **HJR said:**
> Hi, I too am a Linux newbie fighting with the HP P1005.  My address says "serial".  You say to correct it.  How do I do this?  What do I have to replace "serial" with?

The **hplib** package has been updated and **should** support the P1005 printer. This means the serial address may now be a valid address (as it is for my 1000 now). For instance, the address provided by hplib is now: hp:/usb/hp_LaserJet_1000?serial=0.

Before changing the address I would now try to let the automatic process work. Install **hplib** (sudo apt-get install hplib). You said you have tried to install it - make sure the version of hplib is 2.8.2 or later. Run the printer setup from System, Administration, Printers > Add Printers. If you have your printer connected and powered and you have installed hplib it should recognize your printer. 

Here is a link to the HP page which shows 1005 support. There are also install instructions but basically installing hplib through synaptic should be sufficient:
[http://hplip.sourceforge.net/models/laserjet/hp_laserjet_p1005.html]("http://hplip.sourceforge.net/models/laserjet/hp_laserjet_p1005.html")
If it doesn't and it's a usb printer, run "lsusb" to see if the printer is recognized.

Sometimes if I see the print job but nothing prints I have to recycle the power to get my printer to start printing. 

Finally, although you shouldn't need it, to answer your question, you could try substituting "usb://HP/LaserJet%201005" but with the updates of the print drivers I don't believe this will be the solution.

Best of luck.

---

### Post by HJR on 2008-09-10
Thanks for the reply, drs305!

OK, HPLIP is installed with the plugin...

It all goes well until I click "Finish" (in the GUI version of hp-setup).  When I click "Finish", the PC waits for about 2 minutes and then gives this:

cameron@Kulikup:~$ sudo hp-setup
[sudo] password for cameron:

HP Linux Imaging and Printing System (ver. 2.8.7)
Printer/Fax Setup Utility ver. 7.2

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

\error: Channel write error
Traceback (most recent call last):
  File "/usr/share/hplip/ui/setupform.py", line 974, in accept
    if d.isIdleAndNoError():
  File "/usr/share/hplip/base/device.py", line 1857, in isIdleAndNoError
    self.queryDevice(quick=True)
  File "/usr/share/hplip/base/device.py", line 1564, in queryDevice
    status_block = status.StatusType8(self)
  File "/usr/share/hplip/base/status.py", line 1306, in StatusType8
    dev.writePrint("\x1b%-12345X@PJL INFO STATUS \r\n\x1b%-12345X")
  File "/usr/share/hplip/base/device.py", line 2038, in writePrint
    return self.__writeChannel(self.openPrint, data)
  File "/usr/share/hplip/base/device.py", line 2069, in __writeChannel
    raise Error(ERROR_DEVICE_IO_ERROR)
base.g.Error: ('Device I/O error', 12)

The installation does not get any further than this.  What does this mean?

---

### Post by HJR on 2008-09-11
:lolflag:  Thanks for the assistance.  Problem solved!

I found success by removing HPLIP completely from my system and reinstalling manually from the source code tarball (following the instructions on the HP website!).

Then I ran the add printer dialogue in the Printers Config tool, like you suggested.  A reboot and replug and we're in business!

This is a breakthrough for me since I have tried a few times and never was able to print under Linux.  Thanks again!

---

### Post by exXP on 2008-09-20
I down-loaded hplip2.8.9 and installed it.  Now I find that I have to bring up the Device Manager (r click on HP icon) and download the hp-plugin.  Having done this everything prints well  -  and the printed output quality is great  -  however, when I switch off  I have to go through the same rigmarole when I restart.  The device manager shows a firmware item which may be what is required to make the plug-in permanent but I am blocked from downloading it. I could just leave the printer on all the time but I'd rather not.  Does anyone have any suggestions?
exXP (and not going back)

---

### Post by zadstyx on 2008-10-05
OK i installed the printer, went through the hplib setup and it appears to function: printer job does not error out, printer icon shows up and job shows processing, job goes away and nothing prints. 

I have tried to print under hp device manager: same effect. job show successful, but nothing comes out on printer. 

device url shows: hp:/usb/HP_LaserJet_P1005?serial=BB03AXA

if i put his on windows machine i can print across that setup, but i'd like to get windows off my network. help would be appreciated...

detail instruction for this newbe is greatly appreciated.

---

### Post by marshcast on 2008-10-16
> **drs305 said:**
> If you go to System, Admin, Printer, does the address look something like this:
```
usb://HP/LaserJet%201000
```

If it has "serial" somewhere in the address correct it.

When you say "no devices found" is that the result of:
```
lsusb
```

How do you change this? I cant change the URL of my printer, it's just a selection from a list & thats the only one.?

---

### Post by drs305 on 2008-10-16
> **marshcast said:**
> How do you change this? I cant change the URL of my printer, it's just a selection from a list & thats the only one.?

In ubuntu you should be able to go to System, Administration, Printing. If you have one, click on the printer and in the right pane you should see the URI. That being said, the drivers have been updated and HP now provides drivers for the HP Laserjet 1000. With the new drivers, the address *can* include a "serial" address even with a usb printer. For instance, my address is now "hp:/usb/hp_LaserJet_1000?serial=0".

The HP drivers are part of the hplip package available in synaptic. I am not currently using these drivers but I believe after installation there will be a HP menu for changing the settings somewhere in the Main Menu.

---

