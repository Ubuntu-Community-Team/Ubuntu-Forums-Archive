---
title: "Share Printers"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by wildbill46 on 2012-10-17
This seems like it should be really simple.  However, it's been driving me crazy for a while now.  I have two separate machines both running 12.04 connected through a cable modem/router.  Each has a usb connected printer.  Both printers are HP.  I have not found anything that allows me to print from one machine to the other printer.  No matter what I try, it wants authentication.  No matter what username or password I try I get a message indicating the password is incorrect.  I've probably missed something obvious but I could sure use some guidance here.  Thanks in advance.   :mad:

---

### Post by Cope57 on 2012-10-17
Most likely the settings are not for sharing.

You can check by using your browser and typing this:

localhost:631

This will open the cups settings.

---

### Post by wildbill46 on 2012-10-18
OK!  Got one working.  The other is:  HP LaserJet Professional M1212nf MFP.  I have it working from the machine where it is attached and it is shared.  It is also connected via wired connection and has it's own address.  It works from the web with HP ePrint with no problems.  I am unable to get it to work from the other 12.04 machine as a shared printer or from either machine as a network printer.  I'm starting to think it has something to do with the printer even though it's new.  No matter how it is installed as a network printer, it returns a "CUPS failed" message.  It's getting to the point where I only have a couple of random hairs left on my head!   :confused:

---

### Post by wildbill46 on 2012-10-19
SOLVED!  When I upgraded to 12.10 today, everything started working fine and in fact, installed the network printers automatically!:)

---

