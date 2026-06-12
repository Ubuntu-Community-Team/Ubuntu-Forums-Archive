---
title: "Computer slow + fan always on"
date: 2018-08-11
forum: New to Ubuntu
---

### Post by imaginary.duck on 2018-08-11
Hello,

I got the following computer:
Lenovo Legion Y520 39,6 cm (15,6 inch Full HD IPS Matt) Gaming Laptop (Intel Core i7-7700HQ, 16GB RAM, 1TB HDD, 128GB SSD, Nvidia GeForce GTX 1050 4GB).

Currently, I have installed Ubuntu 16.04 LTS.
It takes around 2 minutes (literary) to boot up the computer. 
When everything is running, the fan is always active on full speed all the time.
The fan used to be quite until 1-2 weeks ago. The computer has always been very slow on Ubuntu.

Here is an output of the temperature:
```
[COLOR=#242729][FONT=Consolas]~$ [/FONT][/COLOR]sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +64.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +64.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +61.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +64.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +63.0°C  (high = +100.0°C, crit = +100.0°C)

pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +48.5°C  

iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +37.0°C
```


When I installed Ubuntu, I had to change from RAID/IDE to AHCI according to this blog:
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

Could my problem be anything related to that?
Is there any solution to this?

---

### Post by NM5TF on 2018-08-11
is this a new or used laptop ??

if used, have you checked the air vents for dust clogs ??? 

do you use it on a ***_hard surface_*** or a soft surface....the vents below the laptop are important and they need enough space to suck air. use on a hard surface only...

if this a new laptop, I have seen posts about ***_poor heat paste application_*** from the factory....should be under warranty...take it back

tommy

---

### Post by imaginary.duck on 2018-08-11
> **NM5TF said:**
> is this a new or used laptop ??

if used, have you checked the air vents for dust clogs ??? 

do you use it on a ***_hard surface_*** or a soft surface....the vents below the laptop are important and they need enough space to suck air. use on a hard surface only...

if this a new laptop, I have seen posts about ***_poor heat paste application_*** from the factory....should be under warranty...take it back

tommy

It is quite new. Bought it few weeks ago. 
It is on a glass table. 
Don't have the problem under Windows 10.
Still doing a dual boot.

The fan was off few weeks ago, but now it is always active. 
Few weeks ago, it wasn't that hot in my apartment.
However, now it is super hot in my apartment. Over 30+ degree Celsius!
Could there be some kind of sensor that is overheated and triggers the fan and not getting cold down?

---

### Post by Impavidus on 2018-08-11
15°C rise in the room gives 15°C rise in the computer, unless the fans spin faster. That explains part of it. But I suggest you also check for graphics drivers. Poor graphics drivers mean the computer does things on CPU that it should do on GPU, which makes the computer hot and slow. Don't download drivers manually, use the proprietary drivers utility. There's a lot of documentation about nvidia graphics drivers, but I never looked into it as I don't use nvidia graphics.

---

### Post by imaginary.duck on 2018-08-11
I found the problem and it is Chrome browser.
If the browser is open the fan runs on full speed.
However, if I close the browser and have any number of programs open, the fan is silent.
For instance: if I use Firefox, everything works fine.

I have of course downloaded the latest version of Chrome and updated my system.
Can't understand why it is happening. Maybe a bug?

Annoyingly, the reason why I use Chrome and not Firefox is because I had the exact same problem with Firefox few months ago.
When I switched to Chrome everything went good.
Now the problem is back, but switched browser.

Nonetheless, the computer is still super slow.
I have tried different graphic drivers. Didn't change anything.

---

