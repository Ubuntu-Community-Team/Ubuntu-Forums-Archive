---
title: "Resuming from Hibernation Error"
date: 2015-01-16
forum: New to Ubuntu
---

### Post by Abhisek Maiti on 2015-01-16
My Laptop is Dell Inspiron 3542. I've Ubuntu 14.04 installed on my laptop with proprietary Nvidia 340.65 Driver. I've Intel-Nvidia Hybrid Grphics in my system. When I hibernate the machine it shows some errors**(given below **) for a few seconds. Though it is resuming fine as far I tested, I'd like to know the reason of those errors & wish to solve that if possible. Thank you.

```

[B][  923.855875] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
[  923.855876] PM: Device 00:08 failed to restore: error -19
[  924.782725] i2c_designware INT33C3:00: controller timed out
[ 1697.166736] dpm_run_callback(): pnp_bus_resume+0x0/0xa0 returns -19
[ 1697.166738] PM: Device 00:08 failed to restore: error -19[/B]

```

---

### Post by DuckHook on 2015-01-16
Resuming from hibernate is fraught with pitfalls at the best of times. Consider yourself lucky that you can invoke it. It is no longer turned on by default, so you must have turned it on post-install.

Consider what happens when a system hibernates. It's not only a matter of saving the system state; what do you do about the HW that assumes the system continues to be available? At least in suspend, the OS can still keep system hooks alive. In hibernate, those hooks must die because there's no electricity to keep them alive. Many peripherals, especially if they are primitive, cannot resume elegantly and will just give up the ghost. Therefore, some systems will crash after hibernate, go into kernel panic, or display some very unusual behaviour because they recovered incompletely.

I don't know what the first two lines and last two lines are referring to, but the middle line refers to your touchpad. Sometimes a timeout message is no big deal&#8213;the HW just tries again later. At other times, it means it won't work. Since yours is working, I wouldn't worry about it.

The first two lines and last two lines are identical and refer to your plug-and-play bus. There is an indication that some device that the system has assigned ID 00:08 failed to restore. I have no idea what is on your system so no idea if this is a real problem or just a chimerical one, if real problem, what it might be, etc. Again, if your system is working normally in all other respects, then just ignore this error.

I'm not sure how to advise you on the subject of hibernation itself. It was disabled by default starting around version 11.04 because of the instability that it injected into the system. However, I am personally of the opinion that it is a very useful option especially for laptop users. I would just urge caution, don't rely on it, and assume that a revive could fail at any time. Therefore, use it only as a convenience, save all your data before you hibernate and don't be surprised if it fails.

---

