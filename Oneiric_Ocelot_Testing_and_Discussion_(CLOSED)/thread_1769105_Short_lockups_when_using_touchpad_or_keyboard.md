---
title: "Short lockups when using touchpad or keyboard"
date: 2011-05-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-05-27
Is anyone else experiencing short desktop lockups when using touchpad or keyboard for a while?

E.g.:

* Start glxgears in a terminal
* Use the touchpad for like 30 seconds, or
* Write something for about 30 seconds (just repeat "asdf" over and over again)

Do you see glxgears hanging for short time periods?

Powertop shows me:

```
Top causes for wakeups:
  76.7% (481.3)   PS/2 keyboard/mouse/touchpad interrupt
   4.2% ( 26.5)   [iwlagn] <interrupt>
   3.6% ( 22.3)   [Function call interrupts] <kernel IPI>
   2.5% ( 15.5)   compiz
   2.4% ( 15.3)   kworker/0:1
   2.1% ( 13.4)   [kernel scheduler] Load balancing tick
```

Do you get similar results (whether it locks up or not)?

I just tested this on a hybrid GPU notebook: happening with Nouveau, not happening with Intel (interrupts being about the same).

**Update:**

Seems to be an issue with Nouveau. Second machine (running Natty): total lockup with Nouveau, no problems with nvidia-current.

---

