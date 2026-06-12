---
title: "Wirelessly start up / wake up pc"
date: 2009-07-18
forum: Programming Talk
---

### Post by bs_one on 2009-07-18
I'm currently trying to find a way to wirelessly start up my computer. Meaning: My pc got an internet connection and is shut down or (if it has to be like that and there is no other solution) in sleeping mode and I want to wirelessly, from lets say next door, start up/wake up my computer. But I want to do the waking up with just a rf remote or a cellphone or something like that. I googled a bit about that topic and couldn't find any information about it so now I'm trying it here and asking for help / information if somebody did that before and could help me with it.
Oh and I could try using external hardware or so as well :)
Thanks in advance

bs_one

P.s.: And I'm sorry if this is the wrong sub-forum.

P.p.s.: I'm probably away for 2 weeks now so don't think I'm beeing rude cos I'm not answering please :)

---

### Post by SSTwinrova on 2009-07-18
Wake on LAN/WAN is most likely the solution that you're looking for (the difference being if your cellphone has WiFi and can reach your home's network from wherever you will want to do the waking from vs needing to use the internet in order to reach your computer). Also, you'll need BIOS/NIC support (virtually all newer machines do) enabled to listen for the "magic packet" in order to turn on your computer. I've never set this up myself so I can't provide much more help than that, but now you should at least have a term to search for in Google to help your research efforts.

---

### Post by bs_one on 2009-08-02
Hey thanks for your answer :)
I thought aboutv using WoL already but I wanted to try it in a different kind of way, because I currently can't use the internet with my phone and I do not have Wifi built into my phone. :-/
I wanted to build something lets say with an arduino with an rf feature and when I press a button on a remote from like 10m away it will automatically turn on my pc.

regards bs_one

---

