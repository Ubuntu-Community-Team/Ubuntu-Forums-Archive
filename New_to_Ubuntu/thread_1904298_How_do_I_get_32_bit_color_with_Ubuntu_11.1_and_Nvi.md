---
title: "How do I get 32 bit color with Ubuntu 11.1 and Nvidia 560 card?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by AvocadoMan on 2012-01-04
I am trying to get 32 bit color to work with Ubuntu 11.10 64bit. I have a Nvidia gtx 560 card. The Nvidia x server says I am using driver 280.13 and doesn't show anyway to change from 24 bit color to 32 bit color depth. Is there anyway to do it? Would manually installing the newer 290.1 driver from Nvidia work?

---

### Post by mcduck on 2012-01-04
You are actually using the correct color mode. Even though Windows likes to refer to it as "32-bit colors", it's actually only 24 bits, 8 bits for each of the three color channels.

Actual 32-bit images would include additional 8 bits for Alpha channel (transparency) which wouldn't make any sense when talking about display color since your display isn't transparent... ;)

In other words, there is no such thing as 32-bit display color mode. It's usually 24 bits or less. (And you are lucky if your display actually handles even that much, most TN panels don't...) Or if you happen to have a workstation graphics card and a high-end professional display, you *might* have a 30-bit color mode (10 bits for each three color channels). Most likely you don't, you'd definitely know if you had one, having paid several thousands for such hardware...

---

