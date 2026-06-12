---
title: "Kernel Problems."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-07-27
I know Kernel problems have been asked times infinity before, but do to my general lack of experience with Linux I do not really know if they apply to my case.

Anyway, I have managed to dual-boot Ubuntu on my XP laptop. When I try to load it up however,I get a bunch of coding stuff that is working by itself, until it at lasts ends with a "Kernel Panic-not syncing" message.

I have tried the recovery mode (I believe that is what it is called). I have also tried restarting a bunch of times, so I decided to post the question here. I'd like to at least get Ubuntu to work tonight, so any help is really appreciated.

---

### Post by PmDematagoda on 2008-07-27
When you reach the GRUB menu(the list from which you choose "Ubuntu" or "Ubuntu in Recovery Mode", press "E", then go down to the kernel line and press "E" again, then move to the end of the line and enter this:-
```
noapic
```
after that, press Enter and then boot the modified entry with "B". See if that gets you anywhere.

---

