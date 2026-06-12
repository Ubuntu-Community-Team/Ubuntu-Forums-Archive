---
title: "Intel Wireless Ultimate-N 6300 - slow to connect?"
date: 2011-07-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-07-04
With Natty it almost instantly connected after boot and especially after resume from standby, now it takes almost a minute. :(

This happened around before Alpha 1 came out, but I hadn't enough time to investigate - has anyone else noticed that wireless adapter to connect much slower than before (WPA2)?

---

### Post by lucazade on 2011-07-04
> **MacUntu said:**
> With Natty it almost instantly connected after boot and especially after resume from standby, now it takes almost a minute. :(

This happened around before Alpha 1 came out, but I hadn't enough time to investigate - has anyone else noticed that wireless adapter to connect much slower than before (WPA2)?

noticed also here.
ath5k driver for atheros wifi card is slower to connect at startup.

---

### Post by MacUntu on 2011-07-04
Seems to be a userspace issue then -> just tested the latest Natty kernel in Oneiric and I'm getting the same.

---

### Post by lucazade on 2011-07-04
maybe this:
** (nm-applet:1510): DEBUG: old state indicates that this was not a disconnect 0

is at the beginning of .xsessionerrors

---

### Post by MacUntu on 2011-07-04
Or maybe this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805140](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805140)

Or one of the other hundred "slow to connect" bugs. :D There's only one way: test different network-manager versions and bisect the changes. Boring and time consuming. :|

---

### Post by lucazade on 2011-07-04
> **MacUntu said:**
> Or maybe this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805140](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805140)

Or one of the other hundred "slow to connect" bugs. :D There's only one way: test different network-manager versions and bisect the changed. Boring and time consuming. :|

Sounds good.. That bug report is probably the correct one.
I've seen this issue today for first time after have played a lot with suspend.

---

### Post by MacUntu on 2011-07-05
I built NM without that patch and found no changes. Guess I'll open my own bug report later.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805808](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/805808)

**Update:**

Asked an Ubuntu developer with the same adapter and he's not facing this issue. Too bad.

---

### Post by cariboo on 2011-07-05
I have two access points, my netbook connects on boot to the last one it was connected to fairly quickly, but depending on where I am at home the last one may have a low signal, so I connect to the other one, it takes up to a minute to connect to another AP. This is with the Broadcom wl driver.

---

