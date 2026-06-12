---
title: "initializing a variable in C"
date: 2010-11-05
forum: Programming Talk
---

### Post by jamesbon on 2010-11-05
Following is the way I saw a variable initialized in C
```
static const unsigned int rtl8139_rx_config =
        RxCfgRcv64K |
        (RX_FIFO_THRESH << RxCfgFIFOShift) |
        (RX_DMA_BURST << RxCfgDMAShift);

```
on following link

[http://lxr.free-electrons.com/source/drivers/net/8139too.c#L692](http://lxr.free-electrons.com/source/drivers/net/8139too.c#L692)
I have initialized variables in past but above initialization I could not understand what is it?

---

### Post by MattThLinuxNewb on 2010-11-05
It's setting the result of bitwise-ORing together those 3 expressions to rtl8139_rx_config. The expressions in brackets are left-shifting (moving all the bits to the left) the variable on the left by however many places are in the variable on the right (*Shift).

Look up bit operations in C to make sense of it.

---

### Post by jamesbon on 2010-11-05
I understand BIT operations but I do not understand what is the result of ORing which he is trying to store.What is he trying to achieve.

---

### Post by r-senior on 2010-11-05
Bitwise OR with a mask is typically used to turn specific bits on without affecting the values of other bits:

```

Value  Mask     Result
0001 | 1010 --> 1011 // turns bits 1 and 3 on, leaves 2 and 4 as they were

```

---

