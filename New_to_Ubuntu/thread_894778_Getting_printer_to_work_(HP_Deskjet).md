---
title: "Getting printer to work (HP Deskjet)"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-08-19
I bought an HP Deskjet 4240 for school, and I cannot get it to work.  When I first plugged it in, it claimed that it was set up (albeit with an older driver than the model is) but it refuses to do anything.

When I try to print anything (I have tried printing many different types of things from different apps) the printer icon shows up in the taskbar, then it disappears about 5 seconds later, without the printer even making a noise.

If I right click on the icon while it is up, the only options are 'hide' and 'quit'.  Left-clicking on it brings up a list of print jobs in queue, and the correct job is listed.  But the job disappears after a few seconds, leaving an empty list in the window, corresponding with the print icon disappearing from the taskbar.

How can I get this printer to do its job?

Thanks in advance.

---

### Post by LowSky on 2008-08-19
HPLIP should get everything up and running properly

sudo apt-get install hplip
it might be already installed
look undr System>admin> hplip

---

### Post by ConMan318 on 2008-08-19
It was installed, but I checked the compatibility chart on the hplip site and for this printer, 2.8.5 was needed but already installed was 2.8.2.  So I downloaded the updated source from the site, and it works now.

Thanks a lot.

---

### Post by mexlinux on 2009-11-24
My experience with this printer is really good see:
[It's easier than in Windows]("http://www.mexlinux.com/install-a-printer-is-easier-in-linux-than-windows/")

---

### Post by mexlinux on 2009-11-24
My experience with this printer is really good see:
[It's easier than in Windows]("http://www.mexlinux.com/install-a-printer-is-easier-in-linux-than-windows/")

---

### Post by wethecom on 2010-01-04
hp deskjet d1520
ubuntu 9.10 karmic
works great just plugged it in and it ran

---

