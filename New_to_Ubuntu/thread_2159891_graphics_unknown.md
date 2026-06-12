---
title: "graphics unknown"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by bdubawoop on 2013-07-04
i just installed 12.04lts-64 bit & details sez graphics unknown

i got a ati radeon hd4770 card

searched for that & found a lot of complaints about drivers.

i did find this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

which seems to tell everything but the name of the specific driver.

whats the best way to proceed?

---

### Post by Bashing-om on 2013-07-04
bdubawoop; Hi !

To set your mind at ease:
> ---------
"Graphics: Unknown" is a false report and a known bug. Install the package mesa-utils and the graphics card/driver will be shown.

see:
[https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-07-05
> **bdubawoop said:**
> whats the best way to proceed?

Leave it alone!

If you just installed 12.04, it most likely is 12.04.2 -- which means that you can NOT install AMD restricted drivers for that version of Ubuntu that work with your card.

The drivers that DO work with your card are the default Radeon drivers -- and those were installed as part of initial setup.

---

### Post by exploder on 2013-07-05
+1 on leaving the drivers alone!

---

### Post by bdubawoop on 2013-07-05
thanks, ill leave it alone.

haven't seen any video problems yet anyway.

---

