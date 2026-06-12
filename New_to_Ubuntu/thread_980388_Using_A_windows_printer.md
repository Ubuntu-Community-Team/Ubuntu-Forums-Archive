---
title: "Using A windows printer"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Computerwiz1990 on 2008-11-12
Is it possible to use a Windows printer through a network??

If so, how do i set that up?

---

### Post by jimmy the saint on 2008-11-12
Windows does not make printers

What make/model is your printer?  Does it have an ethernet port?

---

### Post by rbprogrammer on 2008-11-12
Just to be clear, do you mean you have a printer set up to a Windows machine, and you want to remotely print from, lets say, and Ubuntu machine?

I'm sure that's possible, but it might be more trouble than it is worth, in my opinion.  At my house, I have a debian server that as one of its features is being a print server, and that was fairly easy to let a windows machine send a print request to the debian print server.  But sending a print request from a linux machine to a windows print server might be more difficult.

But again, just try and clarify your situation a little bit more.

---

### Post by jimmy the saint on 2008-11-12
if you have an ethernet port in the back of the printer, it may be easier to just plug it into your router and use it as a network printer.  you will have to reinstall it on your windows box, but it makes it super easy to share it with any computers that connect to your network.

---

### Post by rbprogrammer on 2008-11-12
> **jimmy the saint said:**
> if you have an ethernet port in the back of the printer, it may be easier to just plug it into your router and use it as a network printer.  you will have to reinstall it on your windows box, but it makes it super easy to share it with any computers that connect to your network.

Yup, that could work too.  I unfortunately and not as lucky to own a new enough printer to have an ethernet port on it :( ...

---

### Post by Kellemora on 2008-11-12
Hi CW

Make sure the printer on the windows box is SHARED first.

CUPS should already be loaded, but you will need to load the Linux Driver for your printer (if not already installed and if available).

In printer settings you will need:
Description:  Any name you want to recognize this printer by.
Location:  Anywhere you want to say the printer is located.
Device URI:  smb://workgroup/RealComputerNameOnNetwork/SharenameOfPrinter
Make&Model: (this is where you select your installed driver).

TTUL
Gary

---

