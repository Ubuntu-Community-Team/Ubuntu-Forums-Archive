---
title: "sudden shutdown"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by juustahiker on 2012-05-24
I've had this problem for a while now. but it seems to be getting worse now. I am running an alienware aurora mALX R1 laptop and currently using ubuntu 12.04 LTS. it seems that during times of heavy computing (IE online videos) my system will just shut down (like someone held down the power button. no warnings or shut-down sequence ). I doubt its an over heat at this point but haven't ruled it out entirely.
```
~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +83.8°C  (crit = +104.8°C)

nouveau-pci-0300
Adapter: PCI adapter
temp1:        +62.0°C  (high = +100.0°C, crit = +110.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +73.0°C  (high = +100.0°C, crit = +110.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +83.0°C  

```
though it might be a bad ram card I tried memtest 86 but it crashed.

---

### Post by matt_symes on 2012-05-29
Hi

Those temperatures look very high. I suspect it's temperatures causing this problem.

Open a terminal and type

```
watch sensors
```

This will update the sensor readings every couple of seconds. Keep an eye on it.

Re-apply thermal paste between the processor and the heat sink. Ensure there is no dust in the fan and laptop.

If you have more than one memory stick remove one and run memtest. If that one passes, take it out and stick the other one in. Test that one as well.

Kind regards

---

### Post by Dave_in_MD on 2012-05-29
> **matt_symes said:**
> Hi

Those temperatures look very high. I suspect it's temperatures causing this problem.

Open a terminal and type

```
watch sensors
```This will update the sensor readings every couple of seconds. Keep an eye on it.

Re-apply thermal paste between the processor and the heat sink. Ensure there is no dust in the fan and laptop.

If you have more than one memory stick remove one and run memtest. If that one passes, take it out and stick the other one in. Test that one as well.


Kind regards
I vote for the dust obstruction or a fan failure, all 4 temps look high to me.  Compressed air works better than vacuum and brush. just don't go much higher than &#8776;30PSIG

---

### Post by juustahiker on 2012-06-10
all right I'll give that a shot and see if it works thanks for the help.

---

### Post by deadflowr on 2012-06-10
Your temps are very high. I agree that cleaning the fans and vent might help. I also think I could be a loose heatsink connection. I had a similar experience where the system I used ran fine until I tried running a game, one minute into the game the system shutdown, The system gave me an error report and I disassembled the system, looked at the heatsink and noticed it wasn't anchored properly. I had to buy some thermal paste, as I removed the heatsink. after I reassembled the heatsink, and everything, the temp dropped significantly and stablized.

---

