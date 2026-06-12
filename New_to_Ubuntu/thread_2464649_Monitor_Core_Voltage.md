---
title: "Monitor Core Voltage"
date: 2021-07-07
forum: New to Ubuntu
---

### Post by outlaw67 on 2021-07-07
Hi.I have Ubuntu 20.04 server.Is there a way to monitor core voltage ? Thanks

---

### Post by CatKiller on 2021-07-08
It depends what hardware monitoring hardware you've got. There was a brief time when CPUs would self-report their voltage, but the settings were too inaccurate and quirky so the capability got taken out again. Which leaves you with what your motherboard sensors report.

Install **lm-sensors** and run **sudo sensors-detect** to see what you've got.

---

