---
title: "HOWTO Set up Samsung ML-17?0 Printer w/o GUI"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by GrumpySmurf on 2006-04-15
These are the steps I followed to set up my Samsung ML-1740 printer in commandline mode only. I don't have any GUI components installed since this is for my LAN file/print server and I didn't want to install gtk1.2 just for the samsung setup utility.

0. Ensure the cupsys and cupsys-client packages are installed.
1. Obtain Samsung PPD driver from Samsung site - this is a tarball that can be extracted to the local system. Default directory should be 'image' under the current directory.
2. Copy the ppd to the correct directory, /usr/share/cups/model
```

sudo cp /tmp/image/ppd/C/ML-1740spl2.ppd /usr/share/cups/model

```
3. Verify that cups is started and that you can view the available printers.
```

lpinfo -v

```
There should be a line like
```
direct usb://Samsung/ML-1740
```
4. Install the printer using lpadmin. I had to copy the ppd from the cups model directory before it would work.
```

sudo cp /usr/share/cups/model/ML-1740spl2.ppd /etc/cups/ppd/samsung_ml1740.ppd
sudo lpadmin -p samsung_ml1740 -E -v usb://Samsung/ML1740 -m ML-1740spl2.ppd

```
5. Restart cupsys.
6. You should be able to access the printer. From a Windows system, for example, set up a printer to point at the URI:
	[http://ip.ad.dr.ess:631/printers/samsung_ml1740](http://ip.ad.dr.ess:631/printers/samsung_ml1740)

Note that these steps worked for me on my system. Theoretically this should work for other Samsung ML-17XX series printers, or other types of printers as well. Your mileage may vary. See the CUPS documentation for more information and details. This can usually be accessed from:

[http://localhost:631/documentation.html](http://localhost:631/documentation.html)

---

