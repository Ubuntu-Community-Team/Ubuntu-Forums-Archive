---
title: "Serial Communication"
date: 2010-05-18
forum: Programming Talk
---

### Post by vysakh.kurup on 2010-05-18
Hi,


I am new to linux coding...
For one of our project we need a back end code which is reciving the data from serial port whenever it is coming(using interrupt handler).
I have a code which is continuously waiting for a data to come...
How do I modify it to meet our requirement..,or can anybody give me a code..????


Thanks &
regards
Vysakh.

---

### Post by Zugzwang on 2010-05-18
> **vysakh.kurup said:**
> I have a code which is continuously waiting for a data to come...


Why should this be a problem? You can use multi-threading in order to do other stuff while waiting.

---

