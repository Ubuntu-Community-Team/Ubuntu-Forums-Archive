---
title: "Temperature increase in 32-bit or 64-bit"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by smemamian on 2012-07-07
hi

The temperature in the 64-bit and 32-bit CPU is the difference?

---

### Post by cottfcfan on 2012-07-07
What???

---

### Post by smemamian on 2012-07-07
CPU temperatures in Ubuntu 64-bit and 32 bit is the difference?

---

### Post by cottfcfan on 2012-07-07
Sorry I don't understand your question.
If your asking if there is a difference in temperature between 32 bit & 64 bit, I would think the answer is no.

---

### Post by kansasnoob on 2012-07-07
Are you saying that you've tried both and the CPU temp is different between the two?

If so what version of Ubuntu are you using?

Please try to be more specific.

---

### Post by smemamian on 2012-07-07
Sry

I installed Ubuntu 64-bit version, CPU temperature is high!!


Can I install Ubuntu 32-bit will reduce the temperature?


ubuntu 
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-26-generic
GNOME 3.4.1
-----------------------------

Intel® Core™ i7 CPU Q 740 @ 1.73GHz × 8
Nvidia GT 425

---

### Post by kansasnoob on 2012-07-07
> **smemamian said:**
> Sry

I installed Ubuntu 64-bit version, CPU temperature is high!!


Can I install Ubuntu 32-bit will reduce the temperature?


ubuntu 
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-26-generic
GNOME 3.4.1
-----------------------------

Intel® Core™ i7 CPU Q 740 @ 1.73GHz × 8
Nvidia GT 425

I typically run fairly low-end hardware (recycled RAM and such) and I have noticed that 64 bit tends to use much more RAM than 32 bit but I doubt that would increase the CPU temp.

Is this a laptop or a desktop?

---

### Post by kansasnoob on 2012-07-07
I should have asked in my last post, please post the output of:

```
free -m
```

---

### Post by smemamian on 2012-07-07
laptop Vaio F13 HFX

free -m :

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3935       3783        152          0        510       1380
-/+ buffers/cache:       1892       2042
Swap:         3073          0       3073
```
acpi -t:
```

~$ acpi -t 
Thermal 0: ok, 69.0 degrees C
Thermal 1: ok, 69.0 degrees C

```

---

### Post by kansasnoob on 2012-07-07
That's damn HOT!

And I see you only have about 150**MB** of RAM available out of **4GB** so it's time to let things cool off and then try 32 bit to see if it's better!

But you didn't post the hardware info I requested :(

But that's hardware failure HOT!

---

### Post by kansasnoob on 2012-07-07
> **kansasnoob said:**
> That's damn HOT!

And I see you only have about 150**MB** of RAM available out of **4GB** so it's time to let things cool off and then try 32 bit to see if it's better!

But you didn't post the hardware info I requested :(

But that's hardware failure HOT!

Sorry, I'm an idiot. Working on two things. Ignore this part:

**But you didn't post the hardware info I requested**

I'm a dummy, sorry :confused:

---

### Post by kansasnoob on 2012-07-07
I'm not at all comfortable playing around in a laptop so I'm certainly uncomfortable recommending anyone else do so but it's possible that something (probably kernel related) is preventing the cooling fan(s) from running properly.

But, **it is not safe to run at that temp!**

---

### Post by cryptotheslow on 2012-07-07
> **smemamian said:**
> laptop Vaio F13 HFX

free -m :

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3935       3783        152          0        510       1380
-/+ buffers/cache:       1892       **2042**
Swap:         3073          0       3073
```

> **kansasnoob said:**
> ......

And I see you only have about 150**MB** of RAM available out of **4GB** so it's time to let things cool off and then try 32 bit to see if it's better!

......


No, he has 2042MB of RAM available. The RAM being used for disk cache will be made available to applications if required.

This explains it better than I can: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

