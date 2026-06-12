---
title: "Oracle VM Virtualbox"
date: 2010-09-03
forum: Philippine Team
---

### Post by gerryb23 on 2010-09-03
I have files that I need to use from Microsoft Office. Unfortunately, the looks or format of the documents that I have made using MS Office didn't look the same when I opened it and used openoffice. In fact, some of the pictures if not all of them were totally lost. I tried looking up in the internet how to make MS office work in virtual mode (guest) with ubuntu linux as host (because I hated viruses, and I think ubuntu is the best OS to get rid of viruses). When I installed windows XP in virtualbox, it worked fine. However, when I was trying to install MS Office through my USB and tried to copy some files too using my USB, Virtualbox seems not to recognize my USB and can't read from it. Anybody who has an idea how my USB device can be read by Oracle VM Virtualbox? Used Virtualbox 3.2.8 r64453

---

### Post by orlandopasionjr on 2010-09-04
try to visit this link bro.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

look for "Setup VirtualBox USB Support"

---

### Post by jroa on 2010-09-04
Virtualbox forums.

[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by howefield on 2010-09-04
> **orlandopasionjr said:**
> try to visit this link bro.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

look for "Setup VirtualBox USB Support"

This wouldn't be a good tutorial to follow. It is old and contains errors.

If you installed Virtualbox from the Ubuntu repository (OSE edition), it doesn't have USB support, you'd need to download the version corresponding to your edition of Ubuntu from virtualbox.org which does have USB support (PUEL edition).

Differences between the two explained here...
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Download from here...
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by orlandopasionjr on 2010-09-04
Ok.

Try this one.

Go to System> Administration>Users and Groups>
then click manage group and then look for vboxusers. select or highlight vboxusers then click properties. 
On Group ID: (as is na iyon, 123 nakalagay sa akin)
under Group Members, tick the checkbox (name of localhost) then click OK, then reboot. 

kaka-try ko lang kanina, nagwork sa akin.

---

