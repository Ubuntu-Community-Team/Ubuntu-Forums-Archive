---
title: "Disabling wireless bluetooth etc mechanically"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by bjngchn on 2014-03-03
Older computers had a mechanical switch to disable wireless. For some reasons the BB doesn't want to make this possible anymore. For the same reason they have cameras. Anyway, can wireless and bluetooth  be disabled in a way equaivalent to mechanical disabling? For example I can turn on windows and using a hotkey disable wireless, or run linux and do the same. But maybe it is running in a way we can't see. or maybe they don't  run after the computer opens (if configured that way), but until then they remain enabled and emit radiation.... How can we prevent a new installation from trying to connect internet? It doesn't make any sense a new installation tries to connect internet, before computer owner has any chance to modify things. Maybe there is a free wireless internet outside our control. How can we know such a thing doesn't exist (is looking at source code enough, or can there be a hardware way of doing things).

---

### Post by Jason_Gibson on 2014-03-03
I highly recommend sticking to the prescription given because this is what happens when you don't follow the doctor's orders. What are you talking about. What do you want to know?

---

### Post by Bibek on 2014-03-03
> **Jason_Gibson said:**
> I highly recommend sticking to the prescription given because this is what happens when you don't follow the doctor's orders. What are you talking about. What do you want to know?

+ 1

I dont think there is a way to disable it if it doesnt have a switch, you can try taking the laptop apart and throwing the wireless card away if the radiation bothers you :)

---

### Post by Vladlenin5000 on 2014-03-03
The whole premise is ridiculous. that you need to disable radios by hardware otherwise the OS will try to get online no matter what and for doing who knows what... NO, IT WON'T.

---

### Post by deadflowr on 2014-03-03
> How can we prevent a new installation from trying to connect internet? 

There are a lot of users in this section
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
who would love to have that problem.

But you should be able to blacklist any device you want not to connect or function(?).

---

### Post by wildmanne39 on 2014-03-04
Please be mindful of the CoC:
> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.
Thanks

---

### Post by Vladlenin5000 on 2014-03-04
Sure, blacklisting will surely do it, nice and cleanly, but ... really? 
Bluetooth, on one hand, isn't even visible by default let alone connect/pair; and on the other, the WiFi won't connect to any network unless the user explicitly tells it to, not even to an open hotspot.

---

### Post by r.stiltskin on 2014-03-04
> **bjngchn said:**
> How can we prevent a new installation from trying to connect internet? It doesn't make any sense a new installation tries to connect internet, before computer owner has any to chance modify things. Maybe there is a free wireless internet outside our control. How can we know such a thing doesn't exist (is looking at source code enough, or can there be a hardware way of doing things).

If you use the Ubuntu 12.04 Alternate or Server CD you can cancel out of DHCP discovery and then choose to continue to install without configuring networking.

---

