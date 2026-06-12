---
title: "Can't restart"
date: 2016-03-30
forum: New to Ubuntu
---

### Post by jdkcarlson on 2016-03-30
Trusty Tahr on Acer Aspire R5-471T.

After grub, I see the loading dots
. 
.. 
... 
....
..... 
and the screen goes black without turning off and stays that way. This happened after I powered it off because I had no feedback from the touchscreen or touchpad.

I tried booting to recovery mode and then resuming normal boot. I got the message

```
* Starting ACPI daemon
initctl failed
```

After that, I can log in in the terminal but the GUI doesn't start.

What's going on?!

---

### Post by Geoffrey_Arndt on 2016-03-30
Ubuntu could have been running the system disk check daemon (takes up to 10" on large disk) . . and it the system was powered off before finishing, well, this can cause issues afterwards.     The system check only runs once every so many startups (used to be one in forty starts, but this may have changed since I last read up on it).

---

