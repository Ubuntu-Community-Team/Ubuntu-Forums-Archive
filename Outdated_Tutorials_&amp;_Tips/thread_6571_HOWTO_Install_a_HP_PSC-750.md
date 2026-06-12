---
title: "HOWTO: Install a HP PSC-750"
date: 2004-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Allen S on 2004-11-29
This has been a problem in every distro that I have tried. I finally found a way to make it work without to much hassle.

The 1st thing that needs to be done is configure the scanner. To do this you'll need hpoj.

Open a terminal window and using a editor such as pico
sudo pico /etc/apt/sources.list
Uncomment the 2 lines for universe
Save file CTL O 
Close pico CTL X

sudo apt-get update
sudo apt-get install hpoj
After downloading and installing it will start ptal-init install
When ask if you want to scan the parallel ports answer NO
When ask if you want to scan the usb ports answer YES
Just choose the defaults for the rest of the questions.

If you know open xsane or what ever scanner frontend you prefer you should be able to scan.

Close the scanner program of your choice

Reboot the machine - in theroy this should be needed but in my experience if you don't the printer won't work.

Log back in as the same user as before

Computer/System Configuration/Printing
New Printer
Use a detected printer ( the PSC-750 should be listed) highlight it.
Forward
Manufacturer HP
Model PSC 750
Default driver is OK
Apply
You should now have the newly installed PSC-750 show up under printers and you are ready to print.

Using thie procedure I have been able to  get the printer and the scanner to work together as they are suppose to.

Not having any other PSC printers to try I would have to guess that the above would work for about any PSC-xxxx printer from HP as long as there are drivers for it in Ubuntu (Linux)

---

### Post by mapes12 on 2009-08-27
Thank you Allen S

This got the scanner in my HP PSC 750 working immediately :guitar:

---

### Post by wolfgrw on 2009-10-25
Hi! I also have this printer. But i can't get it to use the duplex unit. I now what it is and it is pludgged to the back of the printer. I've installed HPLIP 3.6.9. But i will try HPOJ. Anyway, when i print on both sides, it prints the first page normally and the second one on another sheet but upside down, as if it would print on the second page of the first sheet.
Any ideas?

Regards!

---

### Post by Baji P. on 2010-09-03
In case someone else finds this info useful.

I connected my HP PSC 750 (Printer Scanner Copier) to my Ubuntu 10.04.1 system, when I sat down at to configure the device I found that it had already been recognized & installed. Both the printer & the scanner components.

I went into   **Applications => Graphics => XSane Image Scanner**
clicked on Scan and my document scanned.

Folks it does not get any easier than this.

Long live HP & their fabulous printers & scanners.

---

