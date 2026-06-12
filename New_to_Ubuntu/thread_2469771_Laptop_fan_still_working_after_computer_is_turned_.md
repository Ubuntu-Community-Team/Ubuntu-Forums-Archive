---
title: "Laptop fan still working after computer is turned off Lubuntu 21.10"
date: 2021-12-08
forum: New to Ubuntu
---

### Post by yoshiki2 on 2021-12-08
Hi guys,
I have a dell Inspiron 5555. i use the shutdown button on the menu., but even after the laptop has shutdown the fan keeps running/
is there any quick diagnosis I can run?
Thanks

---

### Post by ActionParsnip on 2021-12-09
If you use
```

sudo shutdown -h now

```
Does it turn off fully

---

### Post by guiverc on 2021-12-09
Also asked at [https://discourse.lubuntu.me/t/laptop-fan-still-working-after-computer-is-turned-off-lubuntu-21-10/2925](https://discourse.lubuntu.me/t/laptop-fan-still-working-after-computer-is-turned-off-lubuntu-21-10/2925)

I noted there that I have & have used some device(s) that keep running the fans if the machine is *warm**/hot* after shutdown, which isn't done by the OS itself, but by the hardware/firmware itself, turning off when the box is cooler (*but taking longer in summer*).

On one such box; replacing the fan made it turn off faster (*it wasn't spinning well it turned out, it was the fan spinning for longer that made me look at why & finally realize the fan was dying..*)

---

### Post by GhX6GZMB on 2021-12-09
Like guiverc said: normal. If the CPU/GPU temperature is high, the fan keeps running.
It's got nothing to do with Linux or other OS', it's HW controlled.
You see it on cars, where the cooling fan keeps running after the engine is off.

---

