---
title: "[SOLVED] Ubuntu 8.10 will not let me remove CD"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by resander on 2008-11-19
I have a blank CD-R in the drive and have pressed the eject button on the drive or clicked 'Eject' from the GUI after right/left? clicking the CD desktop icon. The CD tray shoots out and immediately closes. The problem persists after rebooting. I can get out it by forcing entry to BIOS or by pressing eject before logging in (the tray still closes) and then quickly pressing eject again.

This did not happen for 8.04.

When it happens again (it will), how do I get the CD out using the GUI or command line?

---

### Post by talsemgeest on 2008-11-19
Same kind of thing happening for me. I think I will have to file a bug report. But for me, after shooting open and closing, it seems to work OK for me. Any such luck for you?

---

### Post by Peter09 on 2008-11-19
Its a bug in Intrepid

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316)

---

### Post by talsemgeest on 2008-11-19
Well, at least it is known. Hopefully it is just a matter of time before it is fixed.

---

### Post by resander on 2008-11-19
Thanks for letting me know.
Hmmm, until fixed, an excellent training device for pickpockets...

---

### Post by 3rdalbum on 2008-11-19
Heh. If you enable the Proposed repository and update, you will get the fix. I've observed that the fixed package doesn't entirely fix the problem (certain types of discs with certain programs running will still cause the tray to go back in) but it's better than getting your fingers dragged into the drive. :-D

---

### Post by resander on 2008-11-19
Clicked Update on the taskbar and requested update of everything.
Rebooted. The tray now stays out.

---

### Post by talsemgeest on 2008-11-19
Excellent...

---

