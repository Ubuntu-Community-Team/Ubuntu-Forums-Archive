---
title: "Random Lockups"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-06-20
Hi,
I am using the -19 kernel that was in the updates yesterday or the day before that I think? I am using Hardy. I got nvidia graphics card, and a broadcom wireless. are those causing hardy to lock up? any idea?

---

### Post by gameryoshi600 on 2008-06-20
alright. I updated Grub and also did a dist upgrade, disabled compiz, emerald, and everything else. Now I am never getting the lockups. Must be a compiz fusion problem?

edit: Problem isn't solved as I need an answer.

---

### Post by gameryoshi600 on 2008-06-20
I removed the -19 kernel and so far haven't got a lock up with -18. hopefully the next kernel won't do this.

---

### Post by fatality_uk on 2008-06-20
I am just updating to 19, yikes fingers crossed :|

---

### Post by gameryoshi600 on 2008-06-20
this is now happening in every other kernel for me :( I might do a reinstall.

---

### Post by fatality_uk on 2008-06-20
Before you do that, have you tried running
> top
from a terminal to see what processes are running.
Could all be down to a rouge process tasking cpu!

---

### Post by gameryoshi600 on 2008-06-20
Nothing is eating up any cpu. =/ might be my HDD stopping cause i dropped my laptop. ._.

---

### Post by stalkier on 2008-06-20
> **gameryoshi600 said:**
> Nothing is eating up any cpu. =/ might be my HDD stopping cause i dropped my laptop. ._.

Ouch. I don't think it is totally related although it might be for you in this case. I have random lockups using 8.04 with any kernel even the latest 19. This happens on my desktop NOT my laptop. I am not sure why this happens. I have noticed less lockups using the newest kernel, however. Perhaps it is caused by several things all at once...though I think it is mostly FF3. Seems I always have lockups due to using FF3. Maybe this is just why mine locks up.

---

### Post by gameryoshi600 on 2008-06-20
same with me i usually am opening or I have ff3 opened when it locks up.

---

### Post by dwhitney67 on 2008-06-20
I'm curious about this problem because I have also witnessed it on other systems (namely those running Fedora 8 and 9).

Can one of you tell me if this "lockup" was a complete system lockup, or merely a system lag in accepting user actions (mouse clicks, etc.)?

Were you able to ping your system from another system?  If the Gnome/X11 interface froze, were you able to exit X11 (using ctrl-alt-backspace)?  Could you go to an alternate console (e.g. ctrl-alt-F2)?

Under Fedora, the entire system locked up, as if an application failed to service an interrupt.  To all of the questions presented above, the answers I yielded were all "no".

---

### Post by gameryoshi600 on 2008-06-20
> **dwhitney67 said:**
> I'm curious about this problem because I have also witnessed it on other systems (namely those running Fedora 8 and 9).

Can one of you tell me if this "lockup" was a complete system lockup, or merely a system lag in accepting user actions (mouse clicks, etc.)?

Were you able to ping your system from another system?  If the Gnome/X11 interface froze, were you able to exit X11 (using ctrl-alt-backspace)?  Could you go to an alternate console (e.g. ctrl-alt-F2)?

Under Fedora, the entire system locked up, as if an application failed to service an interrupt.  To all of the questions presented above, the answers I yielded were all "no".

Well I didn't try ctrl-alt-backspace.
But I will try that the next time it happens. I believe it was a complete system lockup but not so sure yet.

---

### Post by dwhitney67 on 2008-06-20
Well, let's hope it doesn't happen again.  I know it has not happened for several weeks on my Fedora 9 laptop.  Back when it did happen, I was using my wireless mouse which has a USB dongle to receive the signals.

If indeed it was the mouse causing the problems, then it could be something with the USB driver, maybe the kernel, or with the experimental X11 library that is being included with later versions of *nix.

P.S.  My laptop has an ATI video chip-set; I do not use Compiz; and my Bluetooth service is not active (I don't need it).

---

### Post by gameryoshi600 on 2008-06-21
well i was on my login screen and it happened. clicked ctrl alt backspace but then it wouldn't do anything.

---

### Post by gameryoshi600 on 2008-06-22
apparently its my harddrive. it always stops then i got to force shutdown then go on then it stops. must be because i dropped my laptop

---

