---
title: "Laptop gets too hot and fan won't stop on Ubuntu 12.10"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by rawa93 on 2012-10-24
Hi,

I've just installed the latest Ubuntu release on my Sony Vaio VPCSB1X9E alongside Windows 7 with wubi and from the moment I boot Ubuntu the fan won't stop and my laptop gets too hot. Secondly, I have issues with my charger. When I plug in my charger the green light on the power button starts flashing and it doesn't charge my laptop.

Before, I had installed Linux Mint 13 Mate and I didn't have this issue with the overheating. Why is that on Ubuntu it happens while Linux Mint is also based on Ubuntu?

I'm not very experienced in Linux but I can run commands and all that. Is there a way to fix this?

I've tried using jupiter but it didn't help either.

Thanks!

rawa93

---

### Post by danielbauwens on 2012-10-24
Well, before (i do not see where it is now in 12.10) In 

System Settings > Power 

There was an option where you could make your fans spin down whenever they could or not.

About the laptop getting to hot make sure your ventilator is not blocked by anything, so that it can vent all the heat out and not build it up.

Hope this can help you a bit.
Daniel

---

### Post by rawa93 on 2012-10-24
Unfortunately, this option doesn't exist in this version. I've removed ubuntu and installed it again and now my laptop won't charge again :S.  I've tried using jupiter as an alternative but even Jupiter is not working.

---

### Post by Warprunner on 2012-10-24
I have a Vaio as well. It did the same thing on me, I think in 11.04 or 11.10. 
What I did was I ran conky. Watched what was running like a hawk. It wound up to be a couple of programs that I killed if I remember correctly.
Since I have gone to 12.04, 12.10 Beta, and no the released version, no probs. But you know I always keep conky up.
Instead of Conky just type Top into the terminal. You can see whats running.
I know not much help but I was able to solve it.
Best of Luck!
Warp

---

### Post by Mark Phelps on 2012-10-25
> **rawa93 said:**
> ... Before, I had installed Linux Mint 13 Mate and I didn't have this issue with the overheating. Why is that on Ubuntu it happens while Linux Mint is also based on Ubuntu? ... 

They are not identical even though they have a lot in common.  Have seen recent threads from others where stuff works OK in Mint 13 but doesn't in Ubuntu 12.10.

Also, they are released at different times -- meaning, kernel versions and/or package versions are liable to be different.

It's good that you just tried out 12.10 instead of upgrading to it -- since there still is NO rollback capability in Ubuntu.  It's generally a bad idea to upgrade to a new Ubuntu version for the first few weeks after it comes out as there are always new bugs.

---

### Post by odibrowne on 2012-12-30
I had the same issue with my Samsung NP355 running an A8 quad core processor. Fan constantly running and getting extremely hot. Finally tried Linux mint 14 cinnemon and getting temperatures which are a lot more modest. After running the  command sensor I got the following  output.

acpitz-virtual-0
Adapter: Virtual device
temp1:        +45.0°C  (crit = +210.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +45.6°C  (high = +70.0°C)
                       (crit = +115.5°C, hyst = +108.0°C)

It would appear to be based on the kernel. I am presently using the kernel
3.5.0-17-generic

---

