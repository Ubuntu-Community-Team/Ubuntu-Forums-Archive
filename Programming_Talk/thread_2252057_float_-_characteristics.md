---
title: "float - characteristics"
date: 2014-11-08
forum: Programming Talk
---

### Post by pauls2 on 2014-11-08
As I understand it a value float is signed by default - it can be either negative or positive without using 'signed float'.

Is that correct? 
Is it better to call it as signed for good programming etiquette?

I am asking because there are circumstances where the user would be entering a negative value for at least one of my float variables.

---

### Post by trent.josephsen on 2014-11-08
Please mention the language when you ask questions like this one.

I've never heard of such a thing as an unsigned float. Most floating-point implementations use the IEEE 754 formats, either by specification (Java, for instance) or because it's implemented in hardware (C, for instance: the standard doesn't mandate IEEE 754, but almost all FPUs implement it). All the IEEE 754 formats are signed.

Don't say "signed float" (or the more likely "signed double"); even if your preferred language accepts such a phrase, it will just confuse people, including yourself six months from now.

---

### Post by pauls2 on 2014-11-09
> **trent.josephsen said:**
> Please mention the language when you ask questions like this one.

I've never heard of such a thing as an unsigned float. Most floating-point implementations use the IEEE 754 formats, either by specification (Java, for instance) or because it's implemented in hardware (C, for instance: the standard doesn't mandate IEEE 754, but almost all FPUs implement it). All the IEEE 754 formats are signed.

Don't say "signed float" (or the more likely "signed double"); even if your preferred language accepts such a phrase, it will just confuse people, including yourself six months from now.


I am sorry, the language is ANSI C. Thank you for your answer. My program will accept latitudes with positive values for Northern latitudes and negative values for southern latitudes. In decimal format the latitudes look like this:
42.6525 and the southern equivalent: -42.6525. 

It has been 30 years since I have coded anything so I wanted to be sure. I looked it up before coming here but it wasn't plain enough for me to be sure.

Again, thank you for your time.

Paul

---

### Post by ofnuts on 2014-11-09
It is easy to write a 5-lines program to test this...

---

