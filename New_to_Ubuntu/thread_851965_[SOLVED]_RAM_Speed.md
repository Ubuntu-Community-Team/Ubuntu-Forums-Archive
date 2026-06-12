---
title: "[SOLVED] RAM Speed"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by intense.ego on 2008-07-07
Ubuntu wasn't starting up so I went to Memtest to see if it was a memory problem. It wasn't a memory problem, and Ubuntu booted up eventually but I found out something interesting.

Memtest lists my RAM as DDR II 166 mhz, even though it is actually 667 mhz. Is it clocked down? or is there a problem with the reading?

I have two ram sticks inside. One, which came preinstalled, is 512mb DDR2 667 mhz (or at least its supposed to be). The other one I added later on and is 2gb DDR2 667mhz. They are just run-of-the-mill ram sticks, nothing fancy like a heatsink. I don't know what brand the first one is (it came preinstalled on my Lenovo Thinkpad T60) but the 2gb stick is PNY.

If the memory is being clocked down, would it be safe to take it to full speed? How do I do this? Would I see performance increases?

Thank you in advance.

---

### Post by reeseslover531 on 2008-07-07
look in your bios to see if there is any underclocking going on.

---

### Post by mcduck on 2008-07-07
That's absolutely normal. Your memory is working at correct speed.

The way memory speeds are marketed can be quite confusing, but for DDR2-667 the actual memory clock speed _is_ 166MHz, and the I/O bus is twice that, 333MHz.

Since DDR2 can transfer 4 bits per memory clock cycle the effective speed is calculated as 166,66... * 4 = 667.

---

### Post by intense.ego on 2008-07-07
> **mcduck said:**
> That's absolutely normal. Your memory is working at correct speed.

The way memory speeds are marketed can be quite confusing, but for DDR2-667 the actual memory clock speed _is_ 166MHz, and the I/O bus is twice that, 333MHz.

Since DDR2 can transfer 4 bits per memory clock cycle the effective speed is calculated as 166,66... * 4 = 667.

Thank you, that clears everything up. I am both relieved and disappointed. Relieved that everything is fine and that I don't have to do any work, but disappointed because I thought there was a possibility I could get a huge performance gain.

---

### Post by schmolch on 2008-08-11
I just went through the same drama.
Thanks for clearing that up so nicely, im relieved :-)

---

