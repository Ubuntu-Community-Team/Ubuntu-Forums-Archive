---
title: "Static virtual serial ports and their control"
date: 2012-10-04
forum: Programming Talk
---

### Post by erupter on 2012-10-04
So I'm able to create temporary virtual serial port pairs with socat and they work.
But since I have to simulate a software running on a real robot with real serial ports, I can't always do the configuration manually (think debugging that way...).
I'd like some way of having the socat ports stick at least in terms of names.
I suppose I can launch socat from my application someway (have to investigate that yet), but I need port names to be constant.

By the way I'm using C.

---

