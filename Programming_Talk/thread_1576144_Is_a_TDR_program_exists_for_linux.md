---
title: "Is a TDR program exists for linux?"
date: 2010-09-16
forum: Programming Talk
---

### Post by asorron on 2010-09-16
I've been looking anywhere for ethernet cable TDR which can check the functionality of an ethernet cable like Fluke Networks company devices, though I dont know if its possible to design such thing for any pc, but it is possbile since the device I got at work have a linux kernel...

Anyone know of such a program, or program in development? I'd be pleased to know of it.

---

### Post by Zugzwang on 2010-09-19
Ok, so you didn't got an answer for two days now. Let's see where this comes from. First of all note that the abbreviation "TDR" is uncommon - my guess is that at least 95% of the people here do not know what it stands for (including me).

In the meantime, I'll make a guess. So you want to diagnose network cables connected to your computer if they are still OK. The fact that some special device capable of doing this runs Linux is unfortunately not relevant - the device is likely to have special hardware on board. My bet is that typical network controllers found in normal computers do not have the functionality necessary for such diagnostic very low-level tasks on chip. This is just a bet, but it is based on similarities found in other pieces of hardware:
[LIST]
[*]Many CD burning devices do not allow simply turning on and off the laser - otherwise there was no necessity to have special writing devices supporting this "lightscribe" stuff.
[*]If I remember correctly, not all wireless network devices can be used to snoop the packets "in the air" (e.g., to crack the WEP passwords). If direct access was possible, again, then these devices would not have this limitation.
[/LIST]

---

