---
title: "&quot;Kernel panic - not syncing: CPU context corrupt&quot; ???"
date: 2008-04-16
forum: Other OS Talk
---

### Post by mips on 2008-04-16
My desktop currently has no OS installed and I tried to boot the latest Puppy cd and get the following error:

```
CPU 0: Machine Check Exception: 0000000000000004
Bank 4: b200000000070f0f
Kernel panic - not syncing: CPU context corruption
```

What does this mean? I swapped all the ram around/out and that is not the issue.

Any ideas?

Btw, I have a AMD Athlon 64 3200+ cpu

---

### Post by berylmichael on 2008-04-17
You might look at the following links to see if this helps but the bottom line is that they replaced the motherboard (possibly with a different model) due to leaking capacitors on it.

Wikipedia Machine Check Exception:
http://en.wikipedia.org/wiki/Machine_Check_Exception[/URL]
and 
Kernel Panic for the AMD64:
[http://kerneltrap.org/node/4993](http://kerneltrap.org/node/4993)

I hope this helps.


Michael

---

### Post by mips on 2008-04-18
Thanks for that.

What I have discovered is that my PSU was on it's way out, my one HD had the click of death and died, last night my second hd developed th click of death and got very hot.

A bit later on I will try updating the BIOS, right now I have to install XP to get a urgent ms-word document out to someone. XP does not seem to bitch about faulty hardware though.

Would be a pity for me to have to get new hardware as I just got 2x1MB ddr400 stick in december for this machine. The ram tests fine as I have swapped it all around and out.

I'm really hoping I can fix this.

---

