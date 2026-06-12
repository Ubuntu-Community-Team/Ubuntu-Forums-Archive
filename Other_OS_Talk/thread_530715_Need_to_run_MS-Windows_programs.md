---
title: "Need to run MS-Windows programs"
date: 2007-08-20
forum: Other OS Talk
---

### Post by pointyblue on 2007-08-20
I need to run some MS Windows programs to update my GPS.

Have tried Wine but even though the programs seem to run smoothly they don't detect the GPS, which is in the USB port.

Do any of you know of a free OS that could perhaps run these Windows programs?

---

### Post by init1 on 2007-08-20
Nope. There is an OS called reactos that tries to be xp compatible, but it is far too unstable to use. Windows is free, it's just not legal that way ;)

---

### Post by Scunizi on 2007-08-20
If ubuntu is the only OS on your machine but you have an old copy of Windows that is functional with the programs you'd like to use, try installing VMWare Server (free) and installl Windows.  You'll be able to run it inside of a window on the desktop.  Most usb devices will be recognized inside of VMWare once you figure out how to tell it to attach the device to the guest windows system.  That's actually pretty easy.

---

### Post by cmat on 2007-08-20
So far it's pretty tricky to use USB devices in WINE. Should consider a dual boot. You should try something called Wine-doors and download the MS C++ runtime libraries. Got a few of my Windows programs not only working but access to external devices. They didn't work with stock WINE.

---

### Post by wolfen69 on 2007-08-21
ever think of running windows?

---

### Post by pointyblue on 2007-08-21
Tried Installing Win98 in VMserver, but Microsoft ActiveSync (the program used to update the GPS) requires Win 2000 or newer to install, so that didn't work...

Downloading ReactOS right now, hopefully it works! Will check out Wine-doors too and post the results in this thread.

---

### Post by kellemes on 2007-08-21
> **pointyblue said:**
> 
Downloading ReactOS right now, hopefully it works! Will check out Wine-doors too and post the results in this thread.

Don't think ReactOS provides a working/stable system.. yet.
I'd try to get a hold on Win2000 (Ebay?) and setup dualboot.

---

### Post by init1 on 2007-08-21
The best way to run Windows apps is with Windows.

---

