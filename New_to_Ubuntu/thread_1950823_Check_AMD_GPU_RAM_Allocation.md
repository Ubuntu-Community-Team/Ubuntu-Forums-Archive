---
title: "Check AMD GPU RAM Allocation"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Starcruiser322 on 2012-04-01
I recently installed Ubuntu 11.10 and it all seems to be working fine, but I was wondering:
I know that Windows allocates a certain amount of RAM based on the amount available (basically what it doesn't need) to be used by the GPU for onboard graphics cards. 
I want to know if there is a way to see if and how much is allocated because the tools I was using to see that before aren't working for Linux OS yet.
Specs: AMD Turion II 2.3 Ghz, 6 GB RAM, ATI M880G onboard graphics with AMD Radeon Mobility 4250

EDIT: Well, not exactly beginner talk... let me know if I need to move it.

---

### Post by idoitprone on 2012-04-01
> **Starcruiser322 said:**
> I recently installed Ubuntu 11.10 and it all seems to be working fine, but I was wondering:
I know that Windows allocates a certain amount of RAM based on the amount available (basically what it doesn't need) to be used by the GPU for onboard graphics cards. 
I want to know if there is a way to see if and how much is allocated because the tools I was using to see that before aren't working for Linux OS yet.
Specs: AMD Turion II 2.3 Ghz, 6 GB RAM, ATI M880G onboard graphics with AMD Radeon Mobility 4250

EDIT: Well, not exactly beginner talk... let me know if I need to move it.

ummmmm. i dont think windows allocate ram for the graphic card, it believe its the hardware itself, or the bios.

method 1
The problem with integrate graphics is that it does not have its own ram, so it takes some of the main ram which is slower than the gddr stuff.

It is simple to calculate the ram used by the computer components

type
```
free -m
```look at your ram specs and subtract it with the total from free -m

Please note: this is not necessary calculate the exact ram usage of you onboard ram, because other computer components may also be part of the difference.
method 2
or some motherboards
allow you to set the graphic memory buffer.

go to the bios and try to find the setting for the intergrated graphic card. There you can find the amount allocated for video memory

---

### Post by Starcruiser322 on 2012-04-01
Thanks for the tip, but now I run into the problem that I was afraid of: NO RAM is allocated, which means I'm using the 256 MB built into the chip. 
My MB doesn't let me customize anything worth a sh**. Just startup options and tests.
Thanks to idiotprone for the answer.

---

### Post by idoitprone on 2012-04-01
> **Starcruiser322 said:**
> Thanks for the tip, but now I run into the problem that I was afraid of: NO RAM is allocated, which means I'm using the 256 MB built into the chip. 
My MB doesn't let me customize anything worth a sh**. Just startup options and tests.
Thanks to idiotprone for the answer.

if the ram is built in, then you better not allocate main memory ram, because you will only add latencies to your card, which means make it slower.

Delicated ram vs onboard ram is a huge difference because delicated ram is faster.

If it using the delicated 256 MB ram then its fine

---

### Post by Starcruiser322 on 2012-04-01
Then why, when I was running Windows 7 and I had 3 GB RAM, did it say that my VRAM was 1406 MB?!
And when I upgraded to 6 GB it said 2746 MB?!

....Forget it. It's Windows. That's the Answer.

---

