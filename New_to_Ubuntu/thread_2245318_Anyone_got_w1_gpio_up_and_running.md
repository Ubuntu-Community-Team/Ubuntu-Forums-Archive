---
title: "Anyone got w1_gpio up and running?"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by maier.m on 2014-09-22
Hi there, has anyone ever got the w1_gpio module up and running? Does this module even work?
When I ```
modprobe w1_gpio
``` the system loads wire.ko and w1_gpio.ko.
dmesg shows ```
Driver for 1-wire Dallas network protocol.
``` which comes from wire.ko. But loading w1_gpio gives just nothing. I would expect something like ```
 w1-gpio w1-gpio: gpio pin 4, gpio pullup pin -1
```. 
Also /sys/bus/w1/devices/ remains clean where I was hoping for w1_bus_master1.

So anyone in for help?

---

