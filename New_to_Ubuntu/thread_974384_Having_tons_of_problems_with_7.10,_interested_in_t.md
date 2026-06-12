---
title: "Having tons of problems with 7.10, interested in trying to install 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by ferniebiker on 2008-11-07
ok so i am running a q6600 nvdia 8XXX (not sure) 4 gig mem ect. desktop

I had win xp originally installed and i added the 64 bit version of ubuntu 7.10 so that it was a dual boot. it worked for a bit but now i get to grub loader and select ubuntu, this is follwed by:

starting up

kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000

i looked up the problem and tried changing splash in grub loader to a number of things such as noapic, i edited out splash ect. nothing worked. what it would do is take me through a bunch of process and then do some sort of system check that would fail. i have no idea why it would just stop working.
any suggestions?

if no one can help with that i am wondering how to get rid of ubuntu 7.10 and install ubuntu 8.10 without fing up windows xp.

thanks in advance

---

### Post by kernelhaxor on 2008-11-07
> **ferniebiker said:**
> 
i am wondering how to get rid of ubuntu 7.10 and install ubuntu 8.10 without fing up windows xp.

 I can't help with ur other problem but to do this , I would try the 8.10 live CD and make sure everything works .. if so, I would erase the partition holding 7.10 and install 8.10 in its place

---

### Post by ferniebiker on 2008-11-07
would i risk erasing grub loader, i am running 2 hard drives, windows on hd0 and ubuntu is on hd1. what is the safest way to do this?

---

### Post by ferniebiker on 2008-11-07
ok so i am now able to make the live cd work by hitting f6 on the main menu and changing the line 
from .../initrd.gz quiet
to .../initrd.gz noapic


now i just want to know how to make it so i can successfully boot ubuntu from grub because 7.10 is all ready installed on my computer.

---

### Post by LowSky on 2008-11-07
Just install it like you would normally, just use the old 7.10 partition. The newer LiveCD will recreate GRUB and everytihng else, no need to worry, Im running a simular set up with my hard drives

---

