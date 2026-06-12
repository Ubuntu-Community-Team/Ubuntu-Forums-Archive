---
title: "Cannot Load Ubuntu.  Suspect graphics problem."
date: 2013-05-14
forum: New to Ubuntu
---

### Post by CharlieB3 on 2013-05-14
I have tried to load Ubuntu and Lubuntu in both 32 and 64 bit and in both install and live CD mode with no joy.  Message in "nonmodest" mode reads:  "Starting Load Fallback Graphic Devices"  and carries the message "Fail".  

I am new to Linux but not new to computers.  I have built a system with a BioStar A75MG board, AMD A4-3400 dual core APU with Radeon HD6410D graphics, 4 GB Corsair RAM, and Seagate 320 GB HDD and would love to run Ubuntu.  I suspect the problem has to do with the Radeon graphics but am clueless as to how to resolve the issue.

---

### Post by Bashing-om on 2013-05-14
CharlieB3; Hi ! Welcome to the forum.
Not known that you implemented the "nomodeset" boot option correctly, but, for our present purpose this alternative will serve as well:
Boot ubuntu, soon as the bios screen clears depress and hold the shift key -> grub boot menu
In this screen arrow down (2nd entry ??) to an entry line containing the phrase "recovery" ->press the enter key for the recovery console
In the recovery console choose "resume normal boot"

Do you now get to the GUI login ? and can you log into ubuntu at this time ? Degraded graphics at this time is OK.

If you can get to the gui desktop, advise us what version of ubuntu you are attempting to install and we will advise on how to install a graphics driver (the installer should have picked it up and installed an appropriate driver).
But we will see what happens.[INDENT=2]
just try'n to help

[/INDENT]

---

