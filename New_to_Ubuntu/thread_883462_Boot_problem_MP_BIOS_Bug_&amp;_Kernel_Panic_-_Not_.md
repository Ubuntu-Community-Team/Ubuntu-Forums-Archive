---
title: "Boot problem: MP_BIOS Bug &amp; Kernel Panic - Not able to load INIT"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by aakashvakil on 2008-08-08
Hello Everyone - 

I installed Ubuntu 8.04 LTS Desktop version on a Intel Dual Core + Realtek combination - single partition and everything was installed successfully. I did the basic checks and confirmed all my hardware and internet connections were working. 

The initial issue was that when I tried shutting down the machine, I got an error like "Kenrel Panic - Not able to sync". The CPU powered off after that but this message kept displaying on monitor. At this point, the applications and hardware was working fine.

Yesterday night I try to start my machine and get this error on start up (I will note down what all i remember)

1. MP_BIOS bug: 8254 timer not connected to IO-APIC kernel panic - not syncing
2. Kernel Panic - Init Failed - try setting init= and try again

I tried restarting the machine, but now it just does not boot. I don't see a BIOS screen nor do I see any GRUB loading activities.

The hardware still works - i get power to monitor, my cd drive works, speakers get power. 

I tried starting the machine from live cd, but does not work. The keyboard also died.

Any suggestions what I should be doing to get this back up?
All help appreciated.
2. 

Regards,
Aakash

---

### Post by decoherence on 2008-08-08
If you don't get a BIOS screen then the problem is definitely hardware related. There's nothing Ubuntu-specific to do. Just open up the case and re-seat everything. If that doesn't bring it back, start taking components out one by one until you get a BIOS screen. If that doesn't work, see if there are any reset switches on your motherboard.

And if THAT doesn't work, I say the motherboard is suspect.

Oh, and you checked that the monitor is plugged in/turned on, yes? (sorry, gotta ask)

---

### Post by aakashvakil on 2008-08-09
Hello Decoherence - 

Firstly thanks for replying and giving me some directions. I did some initial research in Intel forums that if BIOS does not show up, try removing the motherboard battery and re-set it after 20 mins or so. This would ideally force the system to use factory settings for BIOS.

I removed the battery and RAM and set it again after 20 mins and I was able to start the PC.

I did not have to remove any other components.

After starting I had to set the data time again for Ubuntu to start. It did the disc scan and then restarted. It is working as expected now, however, I still get the MP_BIOS Bug - Timer not set to IO APIC. 

Regards,
Aakash

---

### Post by decoherence on 2008-08-11
Does this halt the boot process?

My mother's machine gets a similar error on startup but it boot fine otherwise. Not sure if it's exactly the same as I'm not in front of that computer. Anyway, just wanted to be clear whether or not you still had a booting problem or if you're just seeing this message as you boot?

thanks,

---

