---
title: "kubuntu don't save wallpraper when restart"
date: 2015-08-19
forum: New to Ubuntu
---

### Post by secofshadow on 2015-08-19
hi all,
my problem is when im restart my pc and i Ghose what wallpraper for desktop
and i press apply hi save that walpraper but when im restart my pc he rest to defult
plz plz help

i have kubuntu 15.04

help plz :(

---

### Post by PaulW2U on 2015-08-19
secofshadw, please allow a little more time before you bump your posts.

The user(s) that might have an answer to your problem may not be online at present and may be in a completely different time zone to you.

I have not used Kubuntu 15.04 for any longer than an **hour** so I really can't help but please allow 10 or more hours before bumping any requests for help.

---

### Post by secofshadow on 2015-08-19
ok i wait:KS

---

### Post by Bucky Ball on 2015-08-19
The picture you are using as wallpaper. Where is it? Is it on a partition that is not auto-mounting at boot and you are having to mount the partition manually? If so, if you mount the partition where the pic is, does the wallpaper appear?

---

### Post by secofshadow on 2015-08-19
yes its on [COLOR=#000000]partition : F[/COLOR]

---

### Post by Bucky Ball on 2015-08-19
Well you need to have F mount at boot. Incidentally, 'F' is Win-speak. Please use sda*, sdb*. For instance sd1, sdb5. If you are using Kubuntu, how come you are seeing the drive letters for partition names? 

If the partition is not mounting at boot then we need more detail. Please show the output of this in a terminal for now:

```
sudo blkid
```

---

