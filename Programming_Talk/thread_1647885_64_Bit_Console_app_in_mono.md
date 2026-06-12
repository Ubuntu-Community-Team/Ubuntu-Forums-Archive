---
title: "64 Bit Console app in mono?"
date: 2010-12-18
forum: Programming Talk
---

### Post by GenericUser on 2010-12-18
I am new to Linux, and I am in a programming class.
I have 2 laptops that are both dual-boot Win/Ubuntu 10.10
In class we have been using Microsoft Visual Studio
at home Ive been playing with Mono.
In Visual studio there isn't a 64 Bit console application template.
I am wondering If there is a 64 Bit template for Mono
If there is another thread on this I apologize, I have prayed to the Google Gods, and they gave me no relevant answer.

---

### Post by directhex on 2010-12-18
> **GenericUser said:**
> I am new to Linux, and I am in a programming class.
I have 2 laptops that are both dual-boot Win/Ubuntu 10.10
In class we have been using Microsoft Visual Studio
at home Ive been playing with Mono.
In Visual studio there isn't a 64 Bit console application template.
I am wondering If there is a 64 Bit template for Mono
If there is another thread on this I apologize, I have prayed to the Google Gods, and they gave me no relevant answer.

Mono ignores the 32/64 bit flag on an assembly - it's just a case of which Mono runtime you have, and it'll run using that. So on AMD64 Ubuntu, it'll run as a 64-bit app. On i386 Ubuntu, it's a 32-bit app.

The only way to mark an assembly as 32-bit only or 64-bit only is using corflags.exe from Windows.

---

