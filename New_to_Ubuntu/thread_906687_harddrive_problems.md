---
title: "harddrive problems"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Da Flo-rid-eee-an on 2008-08-31
my computer crashed while i had ubuntu 7.10 on it and it did something to the harddrive so that it wont take any operating system at all on it
 
im not sure what happened and id like to not have to buy a new HD. also it is an older computer (2000ish) and so i was wondering if anyone knew where i could get an adapter for the newer HD hookups to the older ones (40 pin)

---

### Post by Pro-reason on 2008-08-31
> **Da Flo-rid-eee-an said:**
>  where i could get an adapter for the newer HD hookups to the older ones (40 pin)
Not really sure what you're talking about.  IDE versus SATA?

---

### Post by Redache on 2008-08-31
> my computer crashed while i had ubuntu 7.10 on it and it did something to the harddrive so that it wont take any operating system at all on it

Could you explain this further. What happens when you try and install an OS on it?

Can you also give the make of your hard disk as theres tools you can download to check if there is actual physical damage to the disk and if not do a low level format to put it back to a "Factory Default" type setting.

---

### Post by Immolatus on 2008-08-31
I think OP is referring to pata (parallel) interface. and if it just crashed and is 8 years old anyhow, the drive is probably just smoked.

What is the machine?

---

### Post by bobpur on 2008-09-01
> **Da Flo-rid-eee-an said:**
> my computer crashed while i had ubuntu 7.10 on it and it did something to the harddrive so that it wont take any operating system at all on it
 
im not sure what happened and id like to not have to buy a new HD. also it is an older computer (2000ish) and so i was wondering if anyone knew where i could get an adapter for the newer HD hookups to the older ones (40 pin)


First of all, go to [www.distrowatch.com](www.distrowatch.com) and look down the list on the right side of your screen for Gparted, Partition Magic (Pmagic)or System Rescue CD. Burn one of these ISO's to a cd and insert it into your cd player on your computer. Make sure, in the BIOS, that your machine is set to boot from a cd and let it boot your machine. Reformat your drive and all should be fine when you're done. Pay attention to the "Partition Table," I think it's called, to see if that needs fixed. This table sets the beginning and end of "clusters" on your hdd. I suspect, that when you check your hdd, you'll find the partition will show as black with a yellow triangle with an exclamation point in it present on the left. Reformatting will fix this.

As for a SATA to PATA adapter? I don't think they exist. Try [www.newegg.com](www.newegg.com) for a new PATA hdd if one is required. I think you may be alright with the reformat though.

If you have problems, ask here on the forums. You could do damage if you're not sure what you're doing.

Good Luck.

---

