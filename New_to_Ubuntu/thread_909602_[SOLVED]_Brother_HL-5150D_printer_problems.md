---
title: "[SOLVED] Brother HL-5150D printer problems"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Maethoriel on 2008-09-03
Hello everyone,

I am having trouble getting my computer to talk to my Brother HL-5150D USB printer.  My computer is a IBM ThinkPad T60 laptop running Ubuntu 8.04 (and Windows XP as a dual-boot).  I plugged the printer into the USB port, and went to System > Administration > Printing.  The printer configuration window that opened appears to be recognizing the printer-- it has "Brother HL5150-D series" in the Description field and "usb://Brother/HL-5150D%20series" in the Device URI field.  For Make and Model it has "Brother HL-5150D Foomatic/Postscript (recommended)".

However, when I click "Print Test Page", it does not actually print.  It sends it to the print queue, where it sits with the status as "Processing".  The printer does not respond.  Finally, I get a message saying "Not connected?  Printer 'HL-5150D_series' may not be connected."

I'm new to Linux, but usually fairly good with computers.  I tried searching the forums and Google, but I didn't see anyone with the same problem.  Does anyone know what I could try to get it to work?

Thanks!

---

### Post by Shazaam on 2008-09-03
Try this-
Open Firefox and type in this url (local page for cups admin)...
```
http://127.0.0.1:631
```
Try to configure your printer there. If it says no drivers installed I think there are some in Synaptic. Search Synaptic for "Brother"

---

### Post by Maethoriel on 2008-09-17
Hello Shazaam,

Thank you very much for replying, and sorry I didn't post any follow-up information earlier-- I've been pretty busy lately.

I tried what you said and was able to get to the CUPS page just fine.  I still couldn't get anything to print, though.  Finally I got so frustrated I tried printing it from Windows XP (my laptop is a dual-boot) and it wouldn't print from there either.  So I think part of the problem is the printer, because when I try printing in Windows it gives me a paper error even though it's not jamming and there's plenty of paper in it...

Anyway, I realize this isn't a forum about the printer, so I'll figure that one out elsewhere.  However, it's still causing some weird errors in Ubuntu.  Anytime I try to install software, I get an error.  It says "An error occurred.  The following details are provided: E: hl5150dlpr: subprocess post-installation script returned error exit status 127".  This happens with everything I install, even when the printer is not connected.  The "hl5150dlpr" makes it sound like the printer or its driver has something to do with it.  On the "Details" part of the Changes Applied window, it listed out a lot more text.  I saved it in a text file in case it's needed, but it's pretty long.  Does anyone have any insight on what might be happening?

Thanks!

---

### Post by Sef on 2008-09-17
> Anyway, I realize this isn't a forum about the printer, so I'll figure that one out elsewhere.

It's fine to put your problem here.

> I tried what you said and was able to get to the CUPS page just fine. I still couldn't get anything to print, though. Finally I got so frustrated I tried printing it from Windows XP (my laptop is a dual-boot) and it wouldn't print from there either. So I think part of the problem is the printer, because when I try printing in Windows it gives me a paper error even though it's not jamming and there's plenty of paper in it...


Can another device work off of that usb port?  Have you tried other usb ports for your printer?  Do you have another usb cable to check the problem is not with the cable?

---

### Post by Maethoriel on 2008-10-04
Thanks for all the help, everyone-- I really appreciate it.

In my case, it turns out that it was a printer problem with it not being able to feed the paper in correctly and it wasn't a problem with the computer at all.  Once I realized what it was, I got it working.  But I still learned a lot trying to fix it (I was too much of a newb to Linux to even know what CUPS was) and I really appreciate your willingness to help!

~ Maethoriel

---

