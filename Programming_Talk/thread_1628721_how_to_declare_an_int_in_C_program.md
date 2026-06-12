---
title: "how to declare an int in C program"
date: 2010-11-23
forum: Programming Talk
---

### Post by jamesbon on 2010-11-23
On this link I came across
[LXR / The Linux Cross Reference]("http://lxr.linux.no/#linux+v2.6.36/include/linux/pci.h#L299")
integer declaration 
```
 unsigned int    is_added:1;
```I have made C programs and declared integers in them but in the above I see use of 
**:**
What sort of syntax is that?

---

### Post by worseisworser on 2010-11-23
[http://en.wikipedia.org/wiki/Bit_field](http://en.wikipedia.org/wiki/Bit_field)

---

### Post by worksofcraft on 2010-11-23
> **jamesbon said:**
> On this link I came across
[LXR / The Linux Cross Reference]("http://lxr.linux.no/#linux+v2.6.36/include/linux/pci.h#L299")
integer declaration 
```
 unsigned int    is_added:1;
```I have made C programs and declared integers in them but in the above I see use of 
**:**
What sort of syntax is that?

It's the number of bits they want to allocate to it. I'm glad you mentioned it because I completely forgot about bit fields.

Personally I think [subrange types]("http://www.freepascal.org/docs-html/ref/refsu5.html#x27-300003.1.1") like they have in Pascal are a much more versatile concept.

None the less I'm about to go try what happens when I ask for more bits than what fit in an int. I won't keep you in suspense but let you try that on your own if you wanna know the result ;P

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> On this link I came across
[LXR / The Linux Cross Reference]("http://lxr.linux.no/#linux+v2.6.36/include/linux/pci.h#L299")
integer declaration 
```
 unsigned int    is_added:1;
```I have made C programs and declared integers in them but in the above I see use of 
**:**
What sort of syntax is that?

What book are you using for learning C? It's not complete if it doesn't mentions bit fields.

A good one is the one by Harbison and Steele. I think it is still kept up-to-date.

---

### Post by spjackson on 2010-11-23
You would need to have read right to the end of the Structures chapter in K&R to learn about bit-fields, because they are covered on the last 2 pages of that chapter.

---

### Post by jamesbon on 2010-11-23
Are you referring to Chapter 10.

---

### Post by spjackson on 2010-11-23
> **jamesbon said:**
> Are you referring to Chapter 10.
My K&R 2nd edition (ISBN  0131103628) does not have a chapter 10. I was referring to chapter 6 Structures. Here is the Table of Contents [http://www.pearsonhighered.com/educator/product/C-Programming-Language/9780131103627.page](http://www.pearsonhighered.com/educator/product/C-Programming-Language/9780131103627.page)

---

