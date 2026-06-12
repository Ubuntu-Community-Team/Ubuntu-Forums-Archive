---
title: "Epson CX6000 scanner"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by Rob P. on 2012-10-29
I have a basic Hardy 8.04 install (32 bit) and need to add my Epson scanner.  I searched and looked at all the backend fixes and can't for the life of me get it to work.

The OS recognizes the printer and it is set as the default printer.
I don't know if it will print because I don't have ink.  I don't use word processors on this computer so don't really care at this point if it prints or not.  I may in the future want this though.
I DO know it will read my SD cards through the printer so it will read through the USB port.
I do not have install disks for scanner/printer so WINE will not help and is not installed anyway.

I updated my pkgs for sane.
Tried to add the backend fixes in rules - not sure how successful but apparently not because sane still can't find the scanner.  "No devices available."
Using xsane scanimage or xsane scanimage-L both give an error msg of:  "Failed to open device 'scanimage': invalid argument."


What I know:
Alt F2 opens run application command window.
Pkg mgr to update pkgs.
Point & click.


What I need:

Step by step instructs to get this thing to work starting from scratch.

---

### Post by COMECON on 2012-10-29
I would advice you to upgrade to a newer release. They have a newer kernel, with better hardware support. They also have better tools for administrating hardware and installing drivers.
If your Hardy definitively doesn't see your scanner, you could install drivers. Maybe the newer release can install them with Jockey, but I found [this page]("http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=72303&infoType=Downloads&platform=OSF_O_LINUX").
Maybe installing that driver would help you.
I hope it so!
~comecon

---

### Post by Rob P. on 2012-10-29
I can't update to a newer release.  This system is 32 bit and has the minimum RAM, which I can't upgrade to more RAM, for Hardy.  It was a very difficult install because of how antique the hardware is and Hardy is the latest ver. I could get.

I looked at your link and I already had D/L'd the drivers from there.  I reinstalled that package and AMAZING I now have a scanner.

Thanks.  Problem solved.

---

### Post by COMECON on 2012-10-29
Great!
But please, mark the thread as solved (under Tools menu).
Bye!

---

