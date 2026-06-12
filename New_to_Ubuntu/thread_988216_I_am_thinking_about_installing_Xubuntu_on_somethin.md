---
title: "I am thinking about installing Xubuntu on something that I do not know the specs of."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by random turnip on 2008-11-20
I bought a PC for £10 ($20) off a freind, he says it does work, but windows has crashed, so I am going to format the HDD and install Xubuntu.

The Computer ran Windows ME and was bought in either 2000 or 2001.  What are the chances of it having good enough specs to run Xubuntu even though I know the requirements are low, 8 years is a long time for a computer.

---

### Post by taurus on 2008-11-20
You can always try to run it from the Xubuntu LiveCD and see what's the spec of that machine.

---

### Post by random turnip on 2008-11-20
How do I do it (I'm no expert at Ubuntu)?

I already have the live CD, I just wonna know how to check the specs when Xubuntu is loaded.

---

### Post by LowSky on 2008-11-20
want to know the specs, just enter bios at boot, it should mention the processor and how much ram

---

### Post by taurus on 2008-11-20
Boot from the LiveCD.  Then, open a terminal and run

```
sudo lshw
```
That should tell you what you need about that machine.  You can check out the RAM (if the above command hasn't already showed) with

```
free -m
```

---

