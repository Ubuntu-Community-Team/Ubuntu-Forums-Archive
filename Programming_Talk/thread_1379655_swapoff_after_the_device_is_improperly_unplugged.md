---
title: "swapoff after the device is improperly unplugged"
date: 2010-01-12
forum: Programming Talk
---

### Post by life_is_a_garden on 2010-01-12
Hi guys, I have a question about swap devices.

If users improperly unplugged a storage device (SATA) without safely removing it, and one of the partition of the device is a swap device, and has been swapon'd, therefore has an entry in /proc/swaps. I can't do swapoff, because it will simply tell me that the device is not found/invalid.

Is there a way to make linux refresh/detect that the swap device is invalid and remove it from the available list of swaps?

---

