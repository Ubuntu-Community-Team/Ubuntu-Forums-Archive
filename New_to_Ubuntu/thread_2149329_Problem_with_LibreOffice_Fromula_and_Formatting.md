---
title: "Problem with LibreOffice Fromula and Formatting"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by wstay on 2013-05-28
Refering to Screenshot1, the formula: =IF(A8<A9,(A9-A8)*N9,(A8-A9)*N9) in Cell O9, should give a positive answer. What I get is a negative answer in black. I format the Cell 09 as in Screenshot2 where a minus should be in Red. Some other cells with minus are also formated to be in Red but they are in black. 
Is there any explanation for this.
I am using Ubuntu 10.04 and Libreoffice 4.0.2.2.

---

### Post by Locus Kiesselbachi on 2013-05-28
I understand your problem. There is no logic. :(

But there are other red negative numbers, why are they red?

---

### Post by wstay on 2013-05-28
> **Locus Kiesselbachi said:**
> I understand your problem. There is no logic. :(

But there are other red negative numbers, why are they red?

All the red negative numbers are all originally in red when I formatted them to be in red with negative numbers.
After I backup the file to another harddisk, some of them are red and some are black.
I checked their cells formatting and all of them are supposed to be in red with negative numbers.

---

### Post by wstay on 2013-05-29
> **wstay said:**
> All the red negative numbers are all originally in red when I formatted them to be in red with negative numbers.
After I backup the file to another harddisk, some of them are red and some are black.
I checked their cells formatting and all of them are supposed to be in red with negative numbers.

I used luckyBackup 0.35 from Ubuntu to backup my file onto another hard-disk.

---

### Post by Impavidus on 2013-05-29
It's strange. I tried to reproduce your problem on libreoffice 3.5.7.2 (running 12.04 LTS) and I can't. Apart from the fact the if statement doesn't work for me (remarkable, but somewhat understandable as its dutch translation "als" does work and I use the dutch language), I have to use semicolons instead of commas. When I use commas I get "error:508", when I use semicolons (as in "=als(A8<A9;(A9-A8)*N9;(A8-A9)*N9)") it works and I get the correct result. Even that could have something to do with my locale settings, as I use the comma as radix character and the period as thousands separator, so maybe the comma as argument separator works for you.

Besides, instead if this if statement you could use "=abs(A8-A9)*N9". It's mathematically identical and somewhat clearer. Maybe it works better.

---

