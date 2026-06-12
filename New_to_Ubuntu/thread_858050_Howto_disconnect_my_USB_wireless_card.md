---
title: "Howto disconnect my USB wireless card?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by phil81uk on 2008-07-13
Silly question time, as I'm just learning Ubuntu...

I want to disconnect my USB wireless card. I assume I shouldn't just yank it out. How do I safely remove it withoutcausing software issues?

---

### Post by bobnutfield on 2008-07-13
You are correct, it could crash your system if you just remove it.  You should first bring the network connection down.

> sudo ifconfig wlan0 down

That brings your wireless network connection down.  Your wireless may be labled something else, so if you don't know what it is, then type ifconfig on it own and it will report what your wireless network is called.

You can then remove the wireless dongle.

Bob

---

