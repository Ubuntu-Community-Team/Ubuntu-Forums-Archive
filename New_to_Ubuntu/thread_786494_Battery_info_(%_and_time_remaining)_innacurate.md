---
title: "Battery info (% and time remaining) innacurate"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by steven0451 on 2008-05-08
Laptop: Lenovo X61s

I can't seem to be able to re-calibrate the battery meter in ubuntu, it only seems to go up to 77% maximum (on a fairly new battery, when at full charge). This means that when it reaches 0%, my computer still continues for another hour or so...

It might be due to the fact that I have an extended battery for it, however it seemed to work on the beta version of Hardy; it has only recently stopped measuring the battery % accurately.

Can anyone help?

---

### Post by gn2 on 2008-05-08
Try ```
acpi -V
``` in a terminal?

---

### Post by steven0451 on 2008-05-08
> **gn2 said:**
> Try ```
acpi -V
``` in a terminal?

Tried that, it gives the same percentage as the visual battery meter (which is wrong) and half an hour **less** on the remaining time (which is even more inaccurate).

---

### Post by BenjaminGTF on 2011-01-04
I have a similar problem on a Lenovo X61 (not the s, nor a tablet)

The battery itself works okay, seems to give me about two hours of use. But the battery indicator always says I have about 4 hours left up until the battery is critically low, and then it says I have five minutes left. I am running dual boot with vista, and in vista the battery time seems pretty accurate. Not the biggest deal, but it would be nice to have it working completely.

---

