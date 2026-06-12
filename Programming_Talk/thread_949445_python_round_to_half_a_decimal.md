---
title: "python round to half a decimal?"
date: 2008-10-16
forum: Programming Talk
---

### Post by peppe78 on 2008-10-16
Hi!

Need some help? How do i round "half" decimals in python 2.2?
I want:
45.75 = 46.00
45.74 = 45.50
45.25 = 45.50
45.24 = 45.00

if you know what i mean?
Thanks!

OK! I got it (Sorry i couldn´t remember it!)

>>> round(45.75*2)/2
43.0
>>> round(45.74*2)/2
42.5

---

### Post by Nemooo on 2008-10-16
The output you've printed doesn't look like what I'd expect from a rounding. How can it round 45.75 down to 43.0?

Or am I missing something?

---

### Post by kahping on 2008-10-16
> **Nemooo said:**
> The output you've printed doesn't look like what I'd expect from a rounding. How can it round 45.75 down to 43.0?

Or am I missing something?

i think it was a typo. supposed to round to 46.0 & 45.5

---

