---
title: "Booting recovery mode"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by nervous137 on 2008-09-17
can any one point me in the right direction. I can boot in recovery mode with no problem, and selecting resume normal boot, but not the associated generic kernal. Being new I haven't a clue where to start looking.

Thanks

---

### Post by aysiu on 2008-09-17
What happens when you choose the default boot option instead of recovery mode?

---

### Post by nervous137 on 2008-09-17
Thanks for the response. I get the following messages repeated on the screen. (I assume they are are logged somewhere but I don't as yet know where).
ata2.00 cmd a0/00:00:24:00/00:00:00:00:00/a0 tug pio36 in
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen.
Thanks

D

---

### Post by natirips on 2008-09-17
Try reinstalling your kernel from Synaptic (it's called linux-image-**version**.generic) by selecting it for reinstallation.

---

### Post by nervous137 on 2008-09-18
My apologies for the delay. I reinstalled the kernel generic (the newest one)linux-image-2.6.24-21-generic. After that I could only boot using the "live CD". After a bit of messing about I removed the kernels xxx.24-21 generic and xxx.24.19. I am now on xxx.24.15 and all seems to be runnig and booting fine. Would it be because there were more than one kernel available or what. Confused at the moment, but I am up an running again.

---

### Post by natirips on 2008-09-18
I have multiple kernels installed, and I can boot all of them normally without problems. The only issue I've found is that my graphics drivers don't works with realtime (rt) kernel, they only work with generic ones (acctually I only have one rt kernel, all others are different versions of generic one that I kept after updating.

Maybe you have some strange driver(s) issue.

Edit: Or more likey you have compiled something for your kernel version and it doesn't work with other kernels without being recompiled.

---

### Post by nervous137 on 2008-09-18
mmmm being kinda new to this I think the only things I have compiled would be VLC and "Adobe Flash".
Many thanks for your help in this. One quick question, the info during the boot up sequence that flows up the screen, is it logged somewhere?
Once again thank you for your help

---

### Post by natirips on 2008-09-18
If you compiled only that it would cause problems (if it would at all) only when you'd use them because they're not any system-citical processes. However, another idea popped up just now in my head: did you change any hardware recently and/or have you installed the proper (new)kernel version (32/64 bit / sparc)?

Oh, and yes, try System -> Administration -> System Log or something like that (I don't have it in english).

---

### Post by nervous137 on 2008-09-18
Hi No I haven't added any new hardware, and in fact unplugged everything not required right now. I used the linux kernel generic linux-image-2.6.24-20-generic. I have a Dell Inspirion 530s, nothing particular connected to it, a lan connection, VGA monitor, and USB speakers.

---

### Post by natirips on 2008-09-18
Strange... Anyway, if the older kernel is working fine for you than just keep using it. The difference in last digit is nearly insignificant, but may make some hardware run that didn't run with an older one (because linux kernels have 99% hardware drivers integrated in them). However, it would be a significant change if 2.7+.x.y kernel were to be released.

---

### Post by nervous137 on 2008-09-18
Ok That is great, once again thank you very much for your help and patience, it really really is appreciated. I'll keep messing with the system till it breaks again. I'll learn more that way.
D

---

