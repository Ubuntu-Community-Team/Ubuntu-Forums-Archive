---
title: "Epson Perfection 2450 scanner and Xsane application"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by gordonsmall@bellsouth.net on 2008-06-11
I am new to the Ubuntu world, and am gradually working my way thru the various applications.  I have run into a problem using my scanner.  The computer is a AMD 64 bit system (3800) with 1 gig of RAM and plenty of storage.

When I turn on the scanner, a small dialog box opens up with the heading xsane 0.995 - Identifies scanner.  In a moment or two, I am presented with a choice of two devices, one of them being the Epson 2450 scanner.  I select that scanner. After a minute or two I get the following message:

Failure to obtain value of option monitor button: error during drive I/O.

I continue on, and soon another message pops up:Error while reading driver settings /home/gordonsmall/.sane/xsane/EpsonPerfection2450.drc is not a device-rc-file!!! (exclamation points belong to Ubuntu, not to me:)

Just for the heck of it, I continue on, and the application opens up with the acquire button active.  I scan a document, but when I click on the enable color preference, I get a message saying : error during CMS conversion. Could not open scanner ICM profile.  About this time I have to force the application to quit. BTW, it will scan a b&w document, but I can't do much with it once it is scanned.

I have noticed a number of posts about scanners and Ubuntu, but they did not sound quite like my experience.  Any suggestions would be greatly appreciated.

Gordon Small

---

### Post by cariboo on 2008-06-11
In System-->Administration-->Users and Groups add yourself to the scanner group. Log out and then log in again and it should work the way it's supposed to.

Jim

---

### Post by gordonsmall@bellsouth.net on 2008-06-14
Thanks, Jim!  Away from the computer right now, but will definitely give that a try.

Gordon Small

---

### Post by gordonsmall@bellsouth.net on 2008-06-22
> **cariboo907 said:**
> In System-->Administration-->Users and Groups add yourself to the scanner group. Log out and then log in again and it should work the way it's supposed to.

Jim

Finally got back home and tried adding myself to the scanner group.  Seemed to work fine - when I got into the User Privileges, scanners were not checked and I checked that box, restarted the machine, and tried to scan again.  Unfortunately, I still had the same error messages.  When I went to color preferences in Xsane, I got the following message: Error during CMS Conversion. Could not open scanner ICM Profile.

Any other thoughts on where to go from here?

Gordon Small

---

