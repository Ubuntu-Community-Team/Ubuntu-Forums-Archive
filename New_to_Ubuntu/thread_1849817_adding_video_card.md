---
title: "adding video card"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by DarinB on 2011-09-25
Hi I have a friend running lucid on an hp a6114x dual boot with win vista
her monitor keeps going to sleep or "making adjustments" now just crashes on both OS's 
I read that it maybe the video card but it has an onboard one can i add an external one? I have an NVIDIA 1GB video card. Do I have to do something to the bios? or something? 
And Yes the system is set to never sleep... it seems to be hardware I may to a full reinstall of win then lucid to see if that willhelp but i would rather not spent the time.
any ideas????

---

### Post by Paqman on 2011-09-25
> **DarinB said:**
> it has an onboard one can i add an external one?

Yep, just disable the onboard video card in the BIOS after you've fitted the new one.

---

### Post by DarinB on 2011-09-25
is it that easy or do I need some kind of bios upgrade

---

### Post by Paqman on 2011-09-25
It's that easy.

---

### Post by DarinB on 2011-09-25
let me see if i understand put n the new card. and attach the monitor to it! then reboot into bios and pick the new card as the video card? 
will i need to update the bio with some sort of driver? or will that make the new card work on boot?

---

### Post by Paqman on 2011-09-26
Almost:

[LIST=1]
[*]Put new card in
[*]Boot up, go to BIOS, disable the old card
[*]Boot into your OS
[*]Install any drivers the new card will need
[/LIST]

Basically you're disabling the onboard video card, then treating the machine exactly as if you'd installed a new card in a machine with no GPU.

---

### Post by DarinB on 2011-09-26
Ok because I am a new at this...

I hook up the monitor to the new card after i install it before I boot up?

---

### Post by DarinB on 2011-09-27
Ok I am learning the psu was too low for the card. 

I also found out the monitor is the entire problem but only found one online HP post that it was the monitor (and only as a possibility)
a different monitor worked great no problems. 

now to figure out what to recommend to buy?

---

