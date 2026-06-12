---
title: "Utilize muticore processors?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by DFord425 on 2008-06-25
Im wondering does ubuntu 8.04 utilize muti-core processors. I just bought a quad-core processor for a new computer build and i want to put ubuntu or kbuntu on it. And im just curious about how well they utilize a muti-core processor.

---

### Post by avtolle on 2008-06-25
My experience is that the AMD-64 "version" utilizes my multi-core processors fully. I believe that the 32 bit install does as well, from reading other threads on the Forum.

---

### Post by powerpleb on 2008-06-25
I don't know about quad cores but it utilizes my dual core very well. If you open System Monitor there is a graph of CPU load for each individual core.

---

### Post by Canis familiaris on 2008-06-25
In my system Ubuntu seems to utilize both the cores in my Athlon X2 very well.

---

### Post by DFord425 on 2008-06-25
Thats what i was hoping to hear, thank you all.

---

### Post by sayakb on 2008-06-25
You can choose the Processor policy among Performance, Powersave and Dynamic. Download Ubuntu Tweak from getdeb.net which provides a good GUI to change the same. You may also change the policy thru gconf (navigate to the /apps/gnome-power-manager)

---

### Post by NilsHG on 2008-06-25
of course the OS uses both cores, but what most users want and mean by the thread question: does ubuntu strech cpu intensive tasks to utilze all cores. from my experience that does not happen. the software needs to be optimized for multiple cpus. so far all the OS does is using cpu 0 for the first task and cpu 1 for the second so both tasks run normally without delay.

---

### Post by bluepowder7 on 2008-06-25
i've seen all kinds of stuff on my dual-core athlon64.  when i was doing video encoding, some apps pegged only ONE core to 99% and left the other unused (so it was at 5% or 15%).  a different app doing the same type of encoding pegged both cores to over 95% (and did the whole encoding job a bit faster).  same OS, different app.

sometimes, i've seen my cpu use swing from 5 / 95 to 95 / 5, as if the OS is changing cores to prevent one from overheating or something.  it was like a yo-yo, going back and forth. the system monitor graph looked funny when it was doing it.

---

