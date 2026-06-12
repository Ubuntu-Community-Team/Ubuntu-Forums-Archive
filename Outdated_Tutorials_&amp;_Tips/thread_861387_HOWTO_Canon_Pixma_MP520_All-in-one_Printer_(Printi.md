---
title: "HOWTO Canon Pixma MP520 All-in-one Printer (Printing and Scanning)"
date: 2008-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by OttifantSir on 2008-07-16
This is what works for me under Ubuntu 8.04 32-bit:

If you plug in the USB-cable, CUPS will recognize it as an MP520, but will use the MP500-drivers.

First, delete this printer from System -> Administration -> Printers

Go here: [Printer Driver For Linux (debian)](http://software.canon-europe.com/software/0030807.asp?model=) and download **MP520_debian.tar**. This is for printing. Double-click the file/Open in an archive-manager and extract the **cnijfilter-common** and **cnijfilter-mp520series** packages. Double-click/install the **common** package.
Then do the same with the **mp520** package.

Printing is now available on both the local machine, and if you tick the checkbox labelled "Share printers connected to this system" (or something alike. I use Norwegian localization), over network. I have to connect to the localhost of the machine I want to print from to get access to any printer on the network.

To get scanning to work, goto Synaptics and delete any SANE-packages you find (search for **sane**), except for **libsane**.

Now, download **scangearmp-common_1.10-1_i386.deb** and **scangearmp-mp520series_1.10-1_i386.deb**. They can be found here: [ScanGear MP for Linux (2.80)]("http://software.canon-europe.com/software/0028479.asp?model="). Double-click/Install the **common** package first, then the **mp520series** package.

You now have ScanGearMP installed. To use this software, you have to access it through GiMP (File -> Retrieve/Fetch -> ScanGear MP...) or make a menu-item. To do the latter, go to System -> Preferences -> Mainmenu.
Choose Graphics in the left pane. Click '+New launcher' and name the launcher. I use simply "Scanner". In the 'command:'-field, type 'scangearmp'.

Both printing and scanning should now work flawlessly. Unfortunately, there is no way to do document-to-PDF scanning, and there is no utility for printer maintenance through the computer. With the on-printer screen, that's easy anyhow, so it isn't hugely missed.

The copy-part of this multi-function device is built-in to the firmware, so this will work regardless of the unit being plugged in to the computer.

This isn't a very advanced HOWTO, but it works, and that's the goal.

I have no idea how to setup this any other way than this. I had no problems installing these drivers, and everything works perfectly, so I apologize to anyone who does have problems, but I can't help you.

Hope this very newbie-HOWTO helps anyone other than me.

---

### Post by spetey on 2008-08-01
Worked beautifully!  Thanks - I've never had such an easy time printing with linux.  Yay community support!

---

### Post by Pokkulompus on 2008-11-05
Works perfectly! Thank you!:p

---

### Post by Tikhon03 on 2010-09-10
I'm getting the following message when I try to double click and install:

p, li { white-space: pre-wrap; } Could not open 'scangearmp-common_1.10-1_i386.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

What would you suggest?

---

### Post by wayward83 on 2010-11-06
I had the same problem. I solved it by downloading the two deb packages separately from the Aus canon support site here:

[http://support-au.canon.com.au/P/search?model=PIXMA+MP520&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP520&menu=download&filter=0&tagname=g_os&g_os=Linux)

Hope that helps.

---

