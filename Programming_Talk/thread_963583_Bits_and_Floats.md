---
title: "Bits and Floats"
date: 2008-10-30
forum: Programming Talk
---

### Post by Rplus9 on 2008-10-30
I'm not a comp-sci student but I've got a question that's in the weeds.

lets say I've got 64 bits, and I know it's supposed to be a double.

I'm also not using C so I don't have any structures, just bits.

how do I calculate the double?

So far I've got a equation like this

(-1)**S * 2**(exp-bias) * 1.(mantissa).

the Sign bit, S is pretty easy,  however with 11-bits of exp is that just straight bin-dec conversion? 
Same with the mantissa and is there a simple mathematical way to take a number like 54938205 and concatenate it to 1.

without knowing the number beforehand I can't think of how like (1 + 54938205/100000000)

maybe I'm just way off.

---

### Post by jpeddicord on 2008-10-30
Moved to Programming Talk.

---

### Post by Zugzwang on 2008-10-30
It depends on the floating point number encoding of the computer you are using. However, most computers used today follow a standard. 

Look here (includes at least one example):
[http://steve.hollasch.net/cgindex/coding/ieeefloat.html]("http://steve.hollasch.net/cgindex/coding/ieeefloat.html")

---

### Post by pp. on 2008-10-30
[http://en.wikipedia.org/wiki/Double_precision](http://en.wikipedia.org/wiki/Double_precision)

---

### Post by Rplus9 on 2008-10-30
yeah I've seen the Wikipedia but for a non-comp-sci guy it makes a few leaps that I'm not following.

S|  exponent |    mantissa   
1|01010100101|101.52bits.01101

(-1)**S * 2**(exponent-bias) * 1.mantissa

I'm looking at the binary like that, and saying the first one is a sign, the second block is a bin-dec conversion for the exponent and the last is bin-dec for mantissa.

is this approach wrong?  (I understand there could be other ways)

---

### Post by pp. on 2008-10-30
> **Rplus9 said:**
> 
is this approach wrong? 

It is very nearly right. 

The exponent is a binary value, nothing bindec about it. However, you have to compensate for the bias. 

The mantissa also is a binary value. However, you have to add one digit '1' in front of it. That's nothing different than saying that in the mantissa only digits after the 'decimal point' are shown. (Only, in that case, you would have to call it a 'binary point', but no one would understand that.)

---

### Post by Bichromat on 2008-10-30
Each bit of the mantissa multiplies a (negative) power of 2. Just like .4321 = **4***1/10^1 + **3***1/10^2 + **2***1/10^3 + **1***1/10^4,
.1101..47 bits..1 = **1***1/2^1 + **1***1/2^2 + **0***1/2^3 + **1***1/2^4 ... + **1***1/2^52

---

