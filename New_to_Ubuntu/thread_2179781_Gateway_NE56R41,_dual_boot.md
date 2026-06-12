---
title: "Gateway NE56R41, dual boot"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by 8nLkxdz on 2013-10-09
I have a NE56R41 by Gateway.  A friend changed the boot sequence in Win 8 so that it found and booted from the CD.  I had a 10.04 version of Ubuntu that booted from the CD and came up running from the CD.  Then from that we did a hard drive install.  Chose to install side by side with Win8.  This version of Ubuntu was a 32 bit version.  My 64 bit version had a error.  The computer boots up to Ubuntu.  I guess I can chose Win8, but haven't tried yet.

So the installation was relatively straight forward.  

Now the problem is with drivers.  Specifically I have to use an USB wifi card.  Sound does not work.  I'm sure the printer won't work.  None of the routines found to bring up the sound work.  The internal sound card is not found.

I'm assuming the problems are with the Win8 drivers which are different that xp and win 7.  

Does anyone have the sound working within Ubuntu on a Win8 machine.  MS has really made things hard.  

Larry

---

### Post by crip720 on 2013-10-09
Hi I can not help to much, but if you are using 10.04, it is not being updated any more.  I would try to download 12.04.  I think it requires a DVD disc.   Ubuntu does not use Windows drivers, it has its own.  You should be able to choose Win8 or Ubuntu at start up.  Good luck I think you will enjoy Ubuntu once the kinks are worked out.  Colin

---

### Post by Amorphous Serendipity on 2013-10-09
Hi 8nLkxdz,

When you select the side-by-side install, that will  automatically partition the HDD for dual-booting. This means that  Windows 8 is sitting on one partition and Linux is sitting on another.  Because the two operating systems are segregated, drivers from one OS  will not effect the other OS (additionally Ubuntu does not use Windows drivers).

To resolve your driver issues you can simply:
[LIST]
[*]Remove the current Ubuntu partition and replace it with the latest LTS release or the most current release.
[*]Upgrade the Kernel on your current install (NOT RECOMMENDED)
[*]Manually load the needed drivers (again NOT RECOMMENDED)
[/LIST]

Is there a reason you need to use 10.04? If not, I would highly recommend you upgrade.

---

