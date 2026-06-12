---
title: "Questions about conky"
date: 2020-07-27
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-27
Hi everyone,

So I installed conky and somehow have managed to get it to display my cpu temp despite having no idea what I'm doing.

I used the variable hwmon 0 temp 1 which I believe is cpu die temperature? and I believe temp 2 is the same for me but on some processors is a pre-calculated offset value? If anyone can shed any light on that I'd appreciate it.

Also my conkyrc is stored in my home folder but I would like to keep it with all my other config files under ~/.config however I can't find how to specify a new path for conky to look in, I know conky -c [path/to/config] tells conky where to look for a config file but the man page doesn't seem to suggest that the change is permanent?

Any info would be much appreciated.

---

### Post by CatKiller on 2020-07-27
It's not permanent. The config file you specify is the one used for that particular invocation. You don't have to only use one.

[ATTACH=CONFIG]286560[/ATTACH]
This one is actually 7 conkies, and I have two more for time & date elsewhere on my desktop.

For the sensor identification, it depends how many sensors you've got and which order the kernel modules that expose them get loaded in: which one is hwmon0 and which one's hwmon1 can change, depending on kernel updates and other fiddling, but the numbers of the sensors themselves don't tend to change. The sysfs files aren't really files, but you can treat them as if they are: you can look in /sys/class/hwmon to help identify which numbers go with which sensor: some of them have a label.

---

### Post by jcdenton1995 on 2020-07-27
Thanks, yeah the labels under /sys/class/hwmon tell me that 'hwmon 0' is my cpu and number 4 is my gpu, so from that I managed to get conky (love that name) to show both those temperatures, there doesn't seem to be any option to break it down by core though, it looks like the k10temp module only exposes Tdie and Tctl which I guess is just the cpu's overall temperature, although I don't think this is a problem at the moment as I've not seen my temps go much beyond 40°c, I'm assuming I've not got one core doing all the work and getting super hot.

Of course I've got no way of knowing how accurate the readings are but I'm assuming they must be pretty accurate, it cant be that hard to implement something like that in 2020?

---

### Post by CatKiller on 2020-07-27
I think the temperature probe is just connected to the heatspreader, and then there'll be another one in the socket for the motherboard's own readings if it checks them separately. You can read the load on each core, though - the conky on my old Sandy Bridge machine had that - and see the load getting passed from core to core over time to prevent hotspots. It's a bit unwieldy to do that with lots of cores, though.

---

### Post by jcdenton1995 on 2020-07-28
Ah I see, thanks!

---

### Post by NM5TF on 2020-07-29
with conky a lot of things are possible.....

here is a screenie of conkywx...a customizable weather app with a system monitor included......

larger image here [https://imgur.com/a/kS5IcVs](https://imgur.com/a/kS5IcVs)

7 different conky's running simultaneously....

---

### Post by jcdenton1995 on 2020-07-30
> **NM5TF said:**
> with conky a lot of things are possible.....

here is a screenie of conkywx...a customizable weather app with a system monitor included......

larger image here [https://imgur.com/a/kS5IcVs](https://imgur.com/a/kS5IcVs)

7 different conky's running simultaneously....

Wow that's a pretty fancy conky, I would feel like some sort of pilot just by having that on my desktop!

---

