---
title: "Battery Problems"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by shoaibi on 2008-08-16
Okay, this is the deak:

I bought a brand new HP Compaq 6720s a couple of months ago. At start it gave me about 3 hours battery runtime while doing office work and 1 and half hour when listening music or watching movies or playing games... At those times i had Hardy heron and everything same as what i have now...

Recently my laptop battery has started to give me real problems. It gives me runtime of about 30-40 minutes even if i don't do anything, with screen brightness as low as possible, with almost all background processes killed... Even compiz disabled...


Even followed this:
[http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)
 but no use...

I checked and found this, was kindda surprised by comparing this on the internet*, tell me what do you say:
```

00:57:49] shoaibi@cosp-hq ~ $ cd /proc/acpi/battery/C23B/
00:58:09] shoaibi@cosp-hq /proc/acpi/battery/C23B $ cat info 
present:                 yes
design capacity:         393 mAh
last full capacity:      393 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 20 mAh
design capacity low:     4 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           01558 2007/10/06
battery type:            LIon
OEM info:                Hewlett-Packard
00:58:11] shoaibi@cosp-hq /proc/acpi/battery/C23B $ cat state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            290 mA
remaining capacity:      383 mAh
present voltage:         12630 mV
00:59:07] shoaibi@cosp-hq /proc/acpi/battery/C23B $ cat alarm 
alarm:                   unsupported

```
and after a while, when battery shows 100% charged:
```

01:13:37] shoaibi@cosp-hq /proc/acpi/battery/C23B $ cat state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      437 mAh
present voltage:         12499 mV

```

* Here (I compared with this guy's battries):
[http://ubuntu.wordpress.com/2007/04/08/getting-details-about-my-laptop-battery-and-taking-care-of-it/](http://ubuntu.wordpress.com/2007/04/08/getting-details-about-my-laptop-battery-and-taking-care-of-it/)
and he had:
[IMG]http://ubuntu.files.wordpress.com/2007/04/battery-stats.png[/IMG]

---

### Post by Sycron on 2008-08-16
My mother has 6720s too and the battery works just fine. Are you really sure it's a battery related problem ? You may go to a PC service and ask someone.

---

### Post by shoaibi on 2008-08-16
what else could it be? do you see that design capacity? isn't that quite low? can you please check running same commands on her laptop and put here the output?

[EDIT]:
I compared with:
[http://ubuntu.wordpress.com/2007/04/08/getting-details-about-my-laptop-battery-and-taking-care-of-it/](http://ubuntu.wordpress.com/2007/04/08/getting-details-about-my-laptop-battery-and-taking-care-of-it/)

---

### Post by jualin on 2008-08-16
I think that the problem is because the battery has lost performance, something very common with laptop batteries. Look at  the Design Capacity 4400 and your last full charge 3134. To preserve the battery life you need to charge the battery only when it's fully discharged.

---

### Post by shoaibi on 2008-08-16
thats not mine, thats the one with which i compared...

---

### Post by Sycron on 2008-08-16
It seems that is a battery problem. OMG there is a big diference between 4400mAh and 393mAh .. think about it.

If a 4400mAh battery gives you <3.5 hours, a 393 one would give you less than half an hour.

---

### Post by jualin on 2008-08-16
> **Sycron said:**
> It seems that is a battery problem. OMG there is a big diference between 4400mAh and 393mAh .. think about it.

If a 4400mAh battery gives you <3.5 hours, a 393 one would give you less than half an hour.

Wow it has only 393mAH?

---

### Post by shoaibi on 2008-08-16
yes, thats the problem... previously this battery was working fine, and one more thing, now if i plug it out and plug back in, it would be only 60% charged or so...

At the charge at 10%, it says 5hours till full recharge, but as soon as it reaches near 65, 70, it goes 100%.

Should i replace batteries? what would be the cost? and are batteries easy to find?

[EDIT}:
atleast design capacity should be correct or close? should it be?

---

### Post by jualin on 2008-08-16
Batteries are fairly easy to find and cost goes from $60 to $150 depending on the model and the capacity. I am not sure in Pakistan though.

---

### Post by shoaibi on 2008-08-16
to my surprise, i plug out and plugin and see:
```

present:                 yes
design capacity:         1000 mAh
last full capacity:      1000 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 50 mAh
design capacity low:     10 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           01558 2007/10/06
battery type:            LIon
OEM info:                Hewlett-Packard
02:11:58] shoaibi@cosp-hq /proc/acpi/battery/C23B $ cat state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            283 mA
remaining capacity:      418 mAh
present voltage:         12624 mV


```
Plus last time it was 100% charged with i plugged out for 3 seconds, and now its only 39%.

Plus even if batteries has gone out of order, atleast design capacity should be correct or close? should it be?

---

### Post by jualin on 2008-08-16
Design capacity should still show the capacity (something like 4400 mAh), I am not sure why is not showing up.

---

### Post by lavinog on 2008-08-16
> **jualin said:**
> To preserve the battery life you need to charge the battery only when it's fully discharged.

This is not true:
> Lithium-ion batteries should not be frequently fully discharged and recharged ("deep-cycled") like Ni-Cd batteries, but this is necessary after about every 30th recharge to recalibrate any external electronic "fuel gauge" (e. g. State Of Charge meter). This prevents the fuel gauge from showing an incorrect battery charge.
[http://en.wikipedia.org/wiki/Lithium_ion#Guidelines_for_prolonging_Li-ion_battery_life]("http://en.wikipedia.org/wiki/Lithium_ion#Guidelines_for_prolonging_Li-ion_battery_life")

---

### Post by jualin on 2008-08-16
> **lavinog said:**
> This is not true:

[http://en.wikipedia.org/wiki/Lithium_ion#Guidelines_for_prolonging_Li-ion_battery_life]("http://en.wikipedia.org/wiki/Lithium_ion#Guidelines_for_prolonging_Li-ion_battery_life")

That's what I have always heard, and what I have experienced at least, maybe I have had bad luck with batteries.

---

