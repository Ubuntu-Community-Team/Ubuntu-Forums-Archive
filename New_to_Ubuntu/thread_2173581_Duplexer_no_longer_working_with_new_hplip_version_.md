---
title: "Duplexer no longer working with new hplip version --- hp p1606dn, hp-toolbox"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by raequin on 2013-09-10
My HP LaserJet Professional p1606dn was not working reliably until I installed the new version of HPLIP from the HP website.  However, before upgrading HPLIP the printer would print two sided (when I could get the printer to work at all, that is).  Now with the new version, two-sided printing is no longer an option when I go to print something.  In the HP Device Manager ("$ hp-toolbox") the Duplexer is under Print Settings -> Installable Options -> Duplexer Installed.  This radio button is set to Off, and it's grayed out so I can't choose On.  I'd like to know how to get two-sided printing functional again.  This is Ubuntu 12.04.

EDIT: Found the solution here: [https://answers.launchpad.net/hplip/+question/205566](https://answers.launchpad.net/hplip/+question/205566).  This is the synopsis

Duplex option needs to be enabled using cups URL.
1)open following URI in browser
localhost:631/admin/
2) select "Printer" tab and required printer.
3) choose "Maintenance" & "Set Default Options" ->"Options Installed".
Duplex option can be set here.

EDIT 2: I spoke too soon.  The Duplexer Installed radio button is set to "on" now, but when printing a job One-Sided is still the only option in Page Setup.

---

### Post by weclark on 2013-11-22
I had a problem with not being able to select duplex printing for an HP 7525 from Document Viewer.  The solution was to change the Paper size to Letter AutoDuplex.

---

