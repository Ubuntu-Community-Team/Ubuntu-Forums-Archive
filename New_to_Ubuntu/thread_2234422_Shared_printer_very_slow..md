---
title: "Shared printer very slow."
date: 2014-07-14
forum: New to Ubuntu
---

### Post by gordon99 on 2014-07-14
I have just managed, with forum help, to get my Windows 7 desktop connected printer working (wireless) from my Ubuntu OS, which is on a dual booted laptop. The printer is a Canon MG3100.  However, the printer churns out docs. sent for printing from Ubuntu much slower than docs. sent from Windows. Is there a work around to get normal printing speeds from Ubuntu please?

---

### Post by mooreted on 2014-07-14
What printer driver are you using?

Looks like Canon has a Linux printer driver:

[http://support-sg.canon-asia.com/contents/SG/EN/0100393702.html](http://support-sg.canon-asia.com/contents/SG/EN/0100393702.html)

---

### Post by gordon99 on 2014-07-14
Excuse my ignorance in these matters mooreted. Is there just one printer driver, the one on the computer to which the printer is wired, or does each wirelessly connected client computer on a shared network have its own printer driver? The reason I ask, of course, is that the driver you directed me to is for linux OSs  whereas the printer is wire connected to Windows OS. If my Ubuntu OS has its own printer driver by necessity then I will search out what one installed and replace it if it is not one written for Linux.

---

### Post by Vladlenin5000 on 2014-07-14
1. Each one of the computers using the printer have its own driver. From an OS point of view a printer connected locally or networked makes little to no difference. For the OS a printer is a printer.

2. Printing to a locally connected printer - from Windows 7 in your configuration - is always faster than printing from some other machine in the network - from Ubuntu in your configuration - therefore what you're experiencing is *a priori *normal and should be expected.

---

### Post by mooreted on 2014-07-14
Linux needs a driver to be able to configure print jobs for a particular printer and send that data over the network to the printer. You have shared the printer on Windows so you are simply using Windows as the print server, but it is Linux that is doing the actual printing.

The default printer drivers are usually Cups+Gutenprint or HPLIP for HP printers. There are lots of other drivers as well. If the default driver doesn't function well, you can try a different driver.

As stated: Network printing will normally be slower than printing directly from a USB-connected printer.

---

### Post by gordon99 on 2014-07-15
Thank you both for your very clear and informative replies. When I print from Windows OS on the laptop via the Windows desktop the printer
works at an acceptable speed. However, printing from Ubuntu on the laptop is considerably slower. I will follow up the matter of the printer driver used by Ubuntu in case this is giving problems.

---

