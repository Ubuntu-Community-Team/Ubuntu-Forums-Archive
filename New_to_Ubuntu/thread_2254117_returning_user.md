---
title: "returning user"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by armandh on 2014-11-25
I've been away from the forums for some time. 
my wife has loved her Ubuntu 10.04 32 bit laptop never using the original "sucks" Vista boot option
sadly the [never backed up] Hdd gave up the magic pixie dust.
it got a transplant from the spares bin and now sports 14.04 32 bit Ubuntu.
everything looks good except the WiFi, 
now it is [for the moment] back to wired just like it's first switch to Ubuntu.
that was back when Broadcom WiFi was near impossible.

once everyone got over the issues; proprietary drivers worked until several versions back.
this is of course why hers stayed 10.04

I suspect that this is much like the absence of real mode drivers after XP; a security issue!
any suggestions

otherwise my next move is a USB WiFi adaption.
I know that will work but I thought I would ask first

[Presario V 6000 mail order bottom end bait and switch or loss leader] 
on its 3rd battery but still working. used for e-mail and web shopping.

---

### Post by Bucky Ball on 2014-11-25
Please open a terminal and give us the output of this command.

sudo lshw -C network

Thanks. 

Most Broadcom does still work, with a little cajoling. ;)

---

### Post by armandh on 2014-12-01
as luck would have it the wife was not happy [actually no luck needed for that]
She wanted her old Ubuntu back so a quick down load and burn then presto
a 10.04 32 bit reinstalled. 
a quick trip to the driver utility and the Broadcom 43 series driver was downloaded/installed
now the wife is back to preferring Ubuntu over Vista.

[but some how it is still all my fault]

---

### Post by mastablasta on 2014-12-01
how is using a non supported non patched distro less of a security issue than using windows XP? you are now on the same level except you have no antivirus/antimalware installed. old distros have security holes and this is particularly a problem since you use it for mostly we bad shopping. not to mention that windows XP is at least still receiving malware removal tool or whatever that is, while 10.04 is getting nothing for some time now (well aside from server, but you problematic entry point for possible malware is desktop).

new version should have drivers in additional drivers utility or you might be able to install them manually. suggest you play around in live session (maybe with persistence) first and maybe getting it to work. 

th egood news is that the chip worked in 10.04 so it should work now as well. alternatively until you find a better solution you can use 12.04 which is still supported until April 2017.: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Bucky Ball on 2014-12-01
Strongly advise 12.04 LTS or 14.04 LTS, supported until 2017 and 2019 respectively. If the regular Ubuntu with Unity doesn't suit or is to resource hungry, there are lighter alternatives, Xubuntu and Lubuntu (lightweight and lighter respectively) to name two.

---

