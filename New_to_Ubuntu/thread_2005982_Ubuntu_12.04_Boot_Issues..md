---
title: "Ubuntu 12.04 Boot Issues."
date: 2012-06-18
forum: New to Ubuntu
---

### Post by mrshay on 2012-06-18
Hello,

I have a Compaq Presario R3000 with a fresh install of Ubuntu 12.04 on it. It came installed when I bought it. I love the OS, and plan to use it for a long time.

My issue is: When I attempt to start the computer, it loads as far as the purple screen... the Ubuntu name does not show up, just a purple screen. At this point it just stops... and stays there. I need to hold down the power button till it shuts off. When I start it up again, it loads a purple screen with four options. When I hit enter on the first one... it boots fine. I can't remember what it says, the options I mean. One is regular, the second is recovery and so on. This repeats on every start up.

Once it fires up, everything works amazing! General use is perfect, no problems with anything else.

Thank you very much for your time.

Warmest regards,

---

### Post by anewguy on 2012-06-18
That "selection" screen is the grub boot menu.  Do you dual-boot just use Ubuntu only on the system?  Does this only happen after the system has been shutdown, or does it also happen on just a restart?

I might suspect there is something in the hardware - like a slightly loose cable to the disk drive or at the motherboard end, an interface problem, etc..  However, if it runs fine afterwards this would seem to indicate either a glich in the MBR on the disk or in boot in Ubuntu.  It might be worth updating grub again to re-write portions of that to see if it works any better:

- open a terminal window

- type:

sudo update-grub

When that finishes, close everything out and try rebooting.  Post back your results.

Dave ;)

---

### Post by mrshay on 2012-06-18
> **anewguy said:**
> That "selection" screen is the grub boot menu.  Do you dual-boot just use Ubuntu only on the system?  Does this only happen after the system has been shutdown, or does it also happen on just a restart?

I might suspect there is something in the hardware - like a slightly loose cable to the disk drive or at the motherboard end, an interface problem, etc..  However, if it runs fine afterwards this would seem to indicate either a glich in the MBR on the disk or in boot in Ubuntu.  It might be worth updating grub again to re-write portions of that to see if it works any better:
There may be many backups in there, we just want each client-folder be deleted 3 days after we created that folder and copied client's stuff in it.
- open a terminal window

- type:

sudo update-grub

When that finishes, close everything out and try rebooting.  Post back your results.

Dave ;)


I only run Ubuntu.

Thank you so very much Dave! Your solution fixed my issue, and all is working correctly now.

Thank you again. 

Regards,

Shay

---

### Post by anewguy on 2012-06-18
Just glad we could help!

dave ;)

---

