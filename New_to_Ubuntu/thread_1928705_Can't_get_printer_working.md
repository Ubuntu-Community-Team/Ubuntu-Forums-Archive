---
title: "Can't get printer working"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Wheel on 2012-02-20
Hi,
I'm using a Dell XPS 8300 desktop (64 bit).
I'm running Oneiric (64 bit), dual booted with Win 7.
I have an old Panasonic KX-P1124 which has an LPT connector.
I am using an LPT to USB adapter to connect the printer _DIRECTLY_ to my desktop,

After reading through many threads, I'm still confused.

In the add printer dialog, I have 2 initial choices:
  1)Enter URI
  2)Network Printer (with several sub-choices)

How do I determine which to use?

Once I've figured out which to use, how do I figure out what SPECIFIC SYNTAX to enter in the Device URI field?

Are there perhaps Terminal commands I could enter which would return the needed info?

As an experiment, I selected "Enter URI", then entered the first of the 2 offered "examples" given in that dialog box:
  (ipp://cups-server/printers/printer-queue)

It proceeded to allow me to select my make/model of printer and installed the driver.  This seems to have worked fine.
But when I click on "Print Test Page", I get an error  message:  "Can't find cups-server".
The  info offered in the diagnostic troubleshooter was pretty confusing and  although I was able to find "Policies" in Printer Properties and checked  the "Enable" box, this did nothing to fix the problem.

I'm  guessing that is because the "example" given is not appropriate for my  machine, but there may be other settings or issues I'm not considering.

Can anyone help?

---

### Post by Wheel on 2012-02-22
Bump

---

### Post by Azdour on 2012-02-22
Hi,

Normally when you plug in a USB printer Ubuntu is pretty good at identifying the printer and installing the driver (if it knows the printer).

In the Add Printer dialog where you see:

1)Enter URI
2)Network Printer (with several sub-choices)

You should also be seeing your printer to select. I think that Ubuntu is not picking up the printer on USB which may be down to the adapter, I'm not sure.

If you open a terminal, hit Alt+F2 and type gnome-terminal followed by return. Then type lsusb. Can you post the results back here.

The other thing to double check is that the port you are using actually works.

---

### Post by Wheel on 2012-02-22
Thanks for the suggestions.  

I wouldn't have thought to check the port itself. 
Other devices work fine using that port, so that's not the problem.

After reading up some more, I've tried using 4 or 5 different URIs.  Each time it allows me to select my correct make & model, then installs the driver.  When I send the test page to the printer, the error occurs.

"Unable to locate printer"  and  "Destination printer does not exist"  are the two which I keep seeing.

Here's lsusb:

joe@joe-XPS-8300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 04ca:0027 Lite-On Technology Corp. 
Bus 002 Device 004: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 002 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 006: ID 046d:c063 Logitech, Inc. 
Bus 002 Device 007: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
joe@joe-XPS-8300:~$ 


Looks like Device 005 could be the printer, but I read English better than tech.

---

### Post by larrypg on 2012-02-22
Hello,

This might be a shot in the dark but...for the uri put in usb://Panasonic/KX-P1124.  Not sure how the conversion from parallel will change things though.

---

### Post by lhb1142 on 2012-02-22
> **Wheel said:**
> Hi,
I'm using a Dell XPS 8300 desktop (64 bit).
I'm running Oneiric (64 bit), dual booted with Win 7.
I have an old Panasonic KX-P1124 which has an LPT connector.
I am using an LPT to USB adapter to connect the printer _DIRECTLY_ to my desktop,

After reading through many threads, I'm still confused.

In the add printer dialog, I have 2 initial choices:
  1)Enter URI
  2)Network Printer (with several sub-choices)

How do I determine which to use?

Once I've figured out which to use, how do I figure out what SPECIFIC SYNTAX to enter in the Device URI field?

Are there perhaps Terminal commands I could enter which would return the needed info?

As an experiment, I selected "Enter URI", then entered the first of the 2 offered "examples" given in that dialog box:
  (ipp://cups-server/printers/printer-queue)

It proceeded to allow me to select my make/model of printer and installed the driver.  This seems to have worked fine.
But when I click on "Print Test Page", I get an error  message:  "Can't find cups-server".
The  info offered in the diagnostic troubleshooter was pretty confusing and  although I was able to find "Policies" in Printer Properties and checked  the "Enable" box, this did nothing to fix the problem.

I'm  guessing that is because the "example" given is not appropriate for my  machine, but there may be other settings or issues I'm not considering.

Can anyone help?

If you haven't done this already, go to < [http://openprinting.org/printers](http://openprinting.org/printers) > and search for your model (it is there; I checked). Download the appropriate driver for your printer and then install it. Your computer *should* then recognize the printer. (You may have to reboot after the installation of the driver).

If this is not your problem and you do already have the correct driver, then I apologize for this reply. I do hope that it helps you.

Lawrence

---

### Post by Wheel on 2012-02-23
> **larrypg said:**
> Hello,

This might be a shot in the dark but...for the uri put in usb://Panasonic/KX-P1124.  Not sure how the conversion from parallel will change things though.


I tried this and saw pretty much the same thing as when I used one of the other URIs I've tried.  The printer & driver were both identified and installed, but the test page still failed to print.
The comment shown at "Printer State" in Properties says:  "Processing--Waiting for printer to become available."  I even waited for a while just to see if that would change anything.  No luck.

And just for good measure, I tried this as a URI:  
parallel://Panasonic/KX-P1124.
The only difference was the content of "Printer State"..  This time it showed:  "Printer not connected."


> If you haven't done this already, go to < [http://openprinting.org/printers](http://openprinting.org/printers)  > and search for your model (it is there; I checked). Download the  appropriate driver for your printer and then install it. Your computer *should* then recognize the printer. (You may have to reboot after the installation of the driver).

If this is not your problem and you do already have the correct driver,  then I apologize for this reply. I do hope that it helps you.

Lawrence     I looked at this page, but the driver it found seems to be the same one which has already been successfully found/installed.
Until now, I had not rebooted after attempting to set up the printer.  I will try that added step to see if it makes any difference and will report my success back here IF it helps.

---

### Post by Azdour on 2012-02-24
Hi,

The result of lsusb seems to indicate that the parallel converter has been detected and recognised.

To check that your computer is actually seeing the printer through the usb cable and converter you should be able to run the following commands:

usb_printerid /dev/usb/lp0
usb_printerid /dev/usb/lp1

One of the above commands should return your printer's id if it has been detected.

---

### Post by Wheel on 2012-02-24
> **Azdour said:**
> Hi,

The result of lsusb seems to indicate that the parallel converter has been detected and recognised.

To check that your computer is actually seeing the printer through the usb cable and converter you should be able to run the following commands:

usb_printerid /dev/usb/lp0
usb_printerid /dev/usb/lp1

One of the above commands should return your printer's id if it has been detected.


I ran your suggested commands.
Here's what I got:

joe@joe-XPS-8300:~$ usb_printerid /dev/usb/lp0
Error: No such file or directory: can't open '/dev/usb/lp0'
joe@joe-XPS-8300:~$ usb_printerid /dev/usb/lp1
Error: No such file or directory: can't open '/dev/usb/lp1'
joe@joe-XPS-8300:~$ 

There is only one file in this folder:  /dev/usb/hiddev0

I'm not sure why nothing else shows in this folder since I also have Keyboard, Mouse & External HD connected via usb.

---

