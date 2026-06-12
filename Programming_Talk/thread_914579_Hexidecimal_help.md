---
title: "Hexidecimal help"
date: 2008-09-08
forum: Programming Talk
---

### Post by cartisdm on 2008-09-08
I'm working on some homework where I'm doing base conversions.  Actually, I have the whole worksheet done I just don't understand one part.

I'm supposed to convert FACE(base 16) to ________(Base 10)


I know the answer is 64206.   I also know that F=15, A=10, C=12, E=14.  I don't get how those numbers from FACE convert to 64206.  I think I'm having a brain fart because the rest of the entire worksheet was a breeze but for some reason I can't figure out where the number came from.

---

### Post by grepgav on 2008-09-08
Well each position is a power of 16 so it goes

16^3 16^2 16^1 16^0

So if you multiply those by the place value and sum it up you get:

15 (f) * 16^3 = 61440
+
10 (a) * 16^2 = 2560
+
12 (c) * 16^1 = 192 
+
14 (e) * 16^0 = 14
= 64 206

The same method can be used for any base. Good luck

---

### Post by kjohansen on 2008-09-08
(14*16^0)+(12*16^1)+(10*16^2)+(15*16^3)

To go from hex to decimal you multiply the number in each place times 16 raised to power of the place.

Since E is in the lowest place it is place 0.  So E*16^0=14*16^0.  And then you just add up the individual terms.

---

### Post by cartisdm on 2008-09-09
Got in now, thanks guys.  That problem was actually an example but oddly enough we never had to do one like that.  I'm glad I know how to do it now though, thanks!!!

---

