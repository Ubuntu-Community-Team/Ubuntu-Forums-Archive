---
title: "How do I program an electronic cigarette?"
date: 2011-01-29
forum: Programming Talk
---

### Post by Dara Javaherian on 2011-01-29
Hello all,

I recently bought an "e-cigarette" ([link]("http://ecirettesolutions.com/products.php?view=productPage&product=35")), it's a bit boring so I thought I could program it! 

It has a blue LED on the tip that lights up when in use and flashes when charging. There is a USB connection that allows me to charge it, does anyone know if it's possible to mess around with it? :D

Dara

---

### Post by lisati on 2011-01-29
A shot in the dark here: does it show up when you plug it in and put in lsusb?

---

### Post by Dara Javaherian on 2011-01-29
> **lisati said:**
> A shot in the dark here: does it show up when you plug it in and put in lsusb?

Hm, well the output doesn't change when I plug it in so

```
dara@dara-laptop:~$ lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

is the output of both when the device is attached and not attached. Probably not a good sign.

---

### Post by cipherboy_loc on 2011-01-29
How about you plug it in and try dmesg after a short (~10s) pause?


Cipherboy

---

### Post by Dara Javaherian on 2011-01-29
> **cipherboy_loc said:**
> How about you plug it in and try dmesg after a short (~10s) pause?


Cipherboy

Nothing different... I'm starting to think that this isn't possible.

---

### Post by trent.josephsen on 2011-01-29
Almost certainly not.  The circuitry required to do what you describe is incredibly simple; no electronic engineer worth half his salary would waste his time on making it programmable.

Shame, though, really... that would be one cool hack.

---

### Post by Dara Javaherian on 2011-01-29
> **trent.josephsen said:**
> Almost certainly not.  The circuitry required to do what you describe is incredibly simple; no electronic engineer worth half his salary would waste his time on making it programmable.

Shame, though, really... that would be one cool hack.

When you say that it seems so obvious. :lolflag: Thanks everyone though.

---

