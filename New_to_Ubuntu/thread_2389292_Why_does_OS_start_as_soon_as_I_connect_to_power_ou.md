---
title: "Why does OS start as soon as I connect to power outlet?"
date: 2018-04-14
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-04-14
When I want to shutdown the laptop, I first shutdown the OS and then unplug the power supply to laptop.
When I want to turn on the laptop, I engage the power supply and then **press power button** on the laptop, then OS starts.


Form past 2 days, OS starts as soon **as I give power supply to laptop**. I do not have to press power button. Occasionally I get CMOS error during BOOT, and then machine reboots on its own. On the 2nd attempt OS boots just fine.
I have not changed power setting, not installed any new package, not installed any OS update.  But I started using external-monitor.

Any guess why this is happening?


Thanks

---

### Post by bsodx on 2018-04-14
Warning: Possible hardware operation ahead, make sure about the backup and know that I won't be the one guilty if things go awry.

Seems like your CMOS battery is depleted, and you get a fail. It autoreboots because of a default BIOS setting named Auto Reboot. You can try to disable it; if it does not reboot later on after that failure it's not the battery. Usually speaking, depleted CMOS won't make a crash but some cases do. Try getting to the mainboard, plug the CMOS(A circular battery with a slot, easy to find)out. You may need to reach the mainboard. Replace with an another battery. (Here, we find it in computer stores with the name CR2032) Plug it in. If not the answer you may try to reset the BIOS with the jumper indicated in user manual, or putting in battery slot a circular conductive such as coins(never tried but it was featured on a forum) and wait for a few moments.

Hope this helps.

Note that this requires unscrewing your way to the mobo and screwing it back. If you can't, consult your service.

---

### Post by wrongusername2 on 2018-04-14
> **bsodx said:**
> Warning: Possible hardware operation ahead, make sure about the backup and know that I won't be the one guilty if things go awry.

Seems like your CMOS battery is depleted, and you get a fail. It autoreboots because of a default BIOS setting named Auto Reboot. You can try to disable it; if it does not reboot later on after that failure it's not the battery. Usually speaking, depleted CMOS won't make a crash but some cases do. Try getting to the mainboard, plug the CMOS(A circular battery with a slot, easy to find)out. You may need to reach the mainboard. Replace with an another battery. (Here, we find it in computer stores with the name CR2032) Plug it in. If not the answer you may try to reset the BIOS with the jumper indicated in user manual, or putting in battery slot a circular conductive such as coins(never tried but it was featured on a forum) and wait for a few moments.

Hope this helps.

Note that this requires unscrewing your way to the mobo and screwing it back. If you can't, consult your service.

Thanks bsodx.
I think CMOS battery is same as RTC battery. I will replace it and see what happens. This is HP Zbook G1. 

I keep the OS and data on separate disks, and back up regularly using Clone zilla.

---

### Post by bsodx on 2018-04-15
RTC battery=CMOS battery. The usual symptoms should include reset of time and date on each start and a CMOS failure.

---

### Post by wrongusername2 on 2018-04-18
Update:

Today I removed the battery from laptop. Restarted the machine. Gave CMOS error, and then machine successfully rebooted in to OS. This means this is a case of depleted battery.

---

### Post by hrsetrdr on 2018-04-18
I consider that odd that a 5 yr. old laptop would have a depleted battery.   Please update and post back when you get a new battery.

---

