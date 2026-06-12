---
title: "Shared Printer under Ubuntu 12.1 and proper printing from Windows 7"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by janeku2 on 2014-02-20
Hello.
I installed on one machine Ubuntu 12.1 and installed needed drivers for Samsung 2070F multifunction printer.
Also following instructions I installed CUPS in order to enable printer sharing and printing from other computer running Windows 7. Everything goes well, printer was found under network, drivers were installed under Windows, but... When I start printing from Ubuntu it is OK, what I see is what I got. Printing from Windows gives something different: It prints some status lines, every time the same, no matter what document I print. Even when trying to print test page, it print the same thing. 

I must say that during installation of drivers under Windows 7, it did not take ones from network (as it do usual, trying to install shared printer under windows network), but I had to install it from original CD driver for printer.
Installation of drivers under Ubuntu goes well, installing original drivers provided by Samsung,and DL from their web site.

Any idea how to manage this error ?

Regards,

---

### Post by Vladlenin5000 on 2014-02-20
Considering it actually prints from the network then it's hardly a network or server (Ubuntu) issue. Most likely it's a problem in the proprietary driver for Windows - it can work fine locally but not remotely - therefore updating it might be a good idea to start: [http://www.samsung.com/pt/support/model/SL-M2070F/SEE-downloads](http://www.samsung.com/pt/support/model/SL-M2070F/SEE-downloads) 
There's also new firmware: [http://www.samsung.com/pt/support/model/SL-M2070F/SEE-downloads](http://www.samsung.com/pt/support/model/SL-M2070F/SEE-downloads)


(EDIT)

Sorry, haven't noticed this is your first post so here it goes the "Hi, welcome", better later then never ;)

PS - The firmware is to be applied in the Ubuntu PC to where the printer is connected and shared; the driver that warrants an update is the Windows one, at the Windows PCs, running the new version should be enough.

---

### Post by janeku2 on 2014-02-21
Hello. I've been thinking about this upgrade.
ZIP file providing upgrade software is made to be run under Windows (silly isn't it ?) because there is a small program that do the thing of upgrading.
I am relatively new to Ubuntu and I do not know exact way and procedure how to send *.HD file for update to printer via machine that runs ubuntu .
I suppose i have to try to make update on windows machine (lucky me I have laptop so it will be easy for me)
Regards,

---

### Post by Vladlenin5000 on 2014-02-21
The firmware is OS independent and although it can be installed using a Windows tool (default option for a locally connected printer) but can as well be upload via network (read the included instructions) thus achieving a true 'independence'. You can do it via network from your Windows machine - the IP will be the same as the one of the Ubuntu machine where the printer is connected - using the aforementioned procedure.
It shouldn't be a problem for you anyway - in the worst case scenario you can connect as you mentioned and run the tool from Windows - and I would start with the Windows driver update anyway. If it works just leave it

---

### Post by janeku2 on 2014-02-21
OK, here is the situation: Firmaware on official site is the same it is already installed on printer.
So it turns out I have to find other way out.
My image attached to this message [IMG]https://dl.dropboxusercontent.com/u/108920567/Scanned%20Document.jpg[/IMG]show the output of every print from Windows to printer .
I tried every possible driver from Windows to make it possible printing but no use.
Maybe I am making mistake in some settings under Linux ???

Also this scan is made from Linux that shows everything regarding Linux drivers is made well.

Can we do step by step Linux sharing settings for sharing printer under network environment ???

Regards,

---

### Post by Vladlenin5000 on 2014-02-22
The problem is neither in Ubuntu nor in the network printing setting (also Ubuntu). If it connects and prints it's good. Problems may exist in the machine sending the print job. Such problems may or may not be drivers related and in order to troubleshoot it's usually required to completely remove the already installed drivers (in Windows that often means uninstalling AND cleaning the registry), reboot and install only the latest version strictly following the manufacturer's instruction for this specific scenario (printer connected to a remote server) if any, or the community solutions if available.

---

### Post by janeku2 on 2014-02-22
Looks like big problem.
I tried all possible drivers from official web site and no effect at all. Also tried other modes than RAW format to send to printer and tehn got only garbage lines on printed paper.
It looks like I have to search on other forums :(
Greetings,

---

