---
title: "Installing printer drivers fails"
date: 2016-10-18
forum: New to Ubuntu
---

### Post by nick-appelqvist on 2016-10-18
Hi! I tried to search the forum for this specific problem I've got but couldn't find any, so here i go!

I'm trying to install my network printer on my laptop with **Ubuntu 16.10**.
[LIST=1]
[*]I go through System settings -> printers -> add printer. 
[*]The printer is detected (**EPSON XP-215**) with the connection "IPP network printer via DNS-SD". 
[*]When I press "*Forward*" a downloadable driver is presented from Epson, with a license I have to accept. 
[*]When I mark the option for "*accept the license*" and then press "*Forward*" the window closes and another one comes up with recommendations to manually pick a driver from the database. 
[/LIST]

If I go through the **terminal** with the command: **sudo system-config-printer** and redo the same process, this comes up (in the terminal window) after I accepted the license and pressed "*Forward*":
```
filldownloadableDrivers
/usr/share/system-config-printer/install-printerdriver.py:3: PyGIWarning: PackageKitGlib was imported without specifying a version first. Use gi.require_version('PackageKitGlib', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import GLib, PackageKitGlib
Signature key supplied
pk.install_signature
pk.install_signature failed

```

...and again the window to manually pick a driver from the database comes up.

You might ask "*Why don't you just pick manually from the list that comes up?*" -My printer model doesn't exist in the list (XP-215), and I've read that sometimes it works if you pick a model "close" to the one I have, but not even the XP-models exists on that list, so it would be impossible for me to decide what other models are "close" to mine.

Another thing, I've tried picking "*Generic Printer*", and following the recommendations, but in the end the printer can't print out correctly with that setting. Since there are downloadable drivers for my printer that are found and presented by the application, there should not be any problems, but I can't get through that window with the license.

Since this is basically my first time with Ubuntu I have no idea what to do, and I tried to google it but nothing that makes any sense to me comes up. My knowledge in linux based systems is very limited. I've recently installed **Ubuntu 16.10** on my laptop (**Lenovo Thinkpad T430s**).

Anyone know what to do or what to at least try?

/Nick

---

### Post by Geoffrey_Arndt on 2016-10-19
Open Printing shows this:

Download the 64bit Deb file first, . . . . then install the "gdebi" stand-alone package manager (using Synaptic or Ubuntu Software) to easily install this (or any deb) from a non-repo source.  


[http://www.openprinting.org/driver/epson-201302w](http://www.openprinting.org/driver/epson-201302w)

---

### Post by nick-appelqvist on 2016-10-19
Thank you for you answere Geoffrey! I am sorry but you have to explain that abit more step by step -ish with clear instructions.

I've downloaded the 64bit drivers (.deb -file) from the link you've posted. But I can't find "gdebi" or how and what I do to install it?

And IF I manage to install "gdebi", what is the process after? Manually install the .deb drivers or go via the printer app in system settings again?

---

### Post by howefield on 2016-10-19
I would go to the Epson website and download the driver for the printer (a deb package) and install it, which should then show up in the printers "list".

gdebi is not installed by default so you would have to install it with

```
sudo apt install gdebi
``` 

but as you have a recent enough version of Ubuntu you don't have to install extra software to install a local .deb package, just use apt, supposing you have the deb package in your Downloads folder..

```
sudo apt install ~/Downloads/epson-inkjet-printer-escpr_1.6.9-1lsb3.2_amd64.deb
```

change the filename to suit whatever it is that you downloaded.

---

### Post by nick-appelqvist on 2016-10-19
> **howefield said:**
> ```
sudo apt install ~/Downloads/epson-inkjet-printer-escpr_1.6.9-1lsb3.2_amd64.deb
```

change the filename to suit whatever it is that you downloaded.

This worked and the printer was finally added with the right drivers! Thank you very much for the help **howefield**!

Another thing to add, when the printer is detected, it's sometimes detected as a **IPP**-printer and sometimes as a **LPD**-printer. I tried adding both types, but the IPP could never connect after being added, but the LPD method worked just fine. This is a minor thing of course, I'll just use the LPD connection. But I still wonder why that is that the printer is (sometimes) actually detected as IPP, but can't detect it when added through IPP. Well well, if anyone has a guess, please let me know!

My problem (and frustration) is still resolved, thank you again!

---

### Post by Geoffrey_Arndt on 2016-10-20
Nick, per your question . . here are  a couple quick points for future reference & clarity  . .

The best place, from what I''ve seen in installing Epson Drivers for many different Epson models is NOT from the Epson Linux page(s).   Epson doesn't build or maintain the drivers   - - but thankfully openprinting.org does. It is also affiliated with the Linux Foundation & their volunteer project teams that maintain the drivers (with limited assistance from Epson).   In fact, I couldn't find your driver on Epsons site at all, but did find it on openprinting.org.

The gdebi installer (it's a program - a gui program) is available in the standard Ubuntu repositories, but may not be available in the Ubuntu Software application (which excludes many useful programs).   That's why it is still a good idea to use either the CLI (command line or terminal) to install it (sudo apt install synaptic) so one has easier access to those programs (like gdebi).   After it's installed, you just "right-click" on the deb file you've downloaded (using the standard file manager) and you'll get a popup window that asks what program you want to use  . . . just select the gdebi option.   After that, the gui is quite simple and intuitive.

Regarding IPP (Internet Printer Protocol) and LPD (Line Printer Daemon), here is what the "AskUbuntu" website offers:

"LPD is an old standard, IPP is newer.

  Ubuntu uses the Common UNIX Printing System ("CUPS") to handle printing. **CUPS uses the Internet Printing Protocol ("IPP") as the basis for managing print jobs and queues**. Other protocols are also supported (*LPD*, SMB, AppSocket a.k.a. JetDirect), some with *reduced functionality*.

  LPD/LPR is still commonly used and works quite well but it doesn't  provide much control for users on the printer settings per print job.

  Both the LPD and JetDirect/AppSocket protocols can be used over the  Internet today, however neither of these protocols provides  authentication services, access control, and all of the document  management and formatting (including printer-specific commands) must be  handled by the machine sending the document.
  IPP is preferred as it uses bidirectional communication which gives you more feedback and control."

Youtube offers many excellent tutorials about different aspects of Ubuntu including Printer installs.   This video shows the method for installing network printers (which applies to almost all printers these days).   It shows a couple methods that you should know about:

[https://www.youtube.com/watch?v=bRrN3tQzfi0](https://www.youtube.com/watch?v=bRrN3tQzfi0)

---

### Post by howefield on 2016-10-20
> **nick-appelqvist said:**
> This worked and the printer was finally added with the right drivers! Thank you very much for the help **howefield**

You're very welcome, well done on getting your printer going.

---

### Post by nick-appelqvist on 2016-10-20
> **Geoffrey_Arndt said:**
> Nick, per your question . . here are  a couple quick points for future reference & clarity  . .

Thank you Geoffrey for your response and clarity in a lot of concepts that I did not know about!

About the **IPP** and **LPD** connection types; I too gathered the same information as you about the differences (except that video which presented an alternative way of installing the printer), so I understand that LPD (in relation to my needs) is quite enough! I do not need the extra feedback or control that IPP offers.
But my thoughts where not on the specifications of the connection types, but rather why the IPP-type was detected but did not work when added. The printer queue just said "*Unable to detect printer*" (or something within those lines), despite the fact that the application detected and identified the printer as a IPP-connection type printer.

In the long run, I'm just glad that I now can print, but others might get the same problem who really needs the functionality of the **IPP-type** connection. I'm sorry to say that I can't seem to find any log through terminal as to why the application cannot detect the printer after being added, but it just might be me not knowing how to do it.

Again I thank you for the clarity of your answer and explanations of a few concepts.

---

