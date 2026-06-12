---
title: "Convert System.currentTimeMillis() to micro second"
date: 2009-10-19
forum: Programming Talk
---

### Post by hoboy on 2009-10-19
I have to convert System.currentTimeMillis() to micro second in java, and need a help

---

### Post by Arndt on 2009-10-19
> **hoboy said:**
> I have to convert System.currentTimeMillis() to micro second in java, and need a help

Are you asking how many microseconds there are in a millisecond?

---

### Post by hoboy on 2009-10-19
> **Arndt said:**
> Are you asking how many microseconds there are in a millisecond?

yes

---

### Post by Bachstelze on 2009-10-19
1 ms = 1,000 µs

---

### Post by hoboy on 2009-10-19
> **Bachstelze said:**
> 1 ms = 1,000 µs

tks

---

### Post by Arndt on 2009-10-19
> **hoboy said:**
> yes

You will find many good explanations if you google for "milli micro". You can also look in your physics book.

---

### Post by hoboy on 2009-10-19
> **Arndt said:**
> You will find many good explanations if you google for "milli micro". You can also look in your physics book.

Well the problem is that i am not studying phisics, it was pure programming task.
I have some milliseconds I want to have the correspondant to in microsec..
i have just mutilpied it now.
1 milliseconds give mive me 1*1000 microsecond
tks.

---

### Post by Arndt on 2009-10-19
> **hoboy said:**
> Well the problem is that i am not studying phisics, it was pure programming task.
I have some milliseconds I want to have the correspondant to in microsec..
i have just mutilpied it now.
1 milliseconds give mive me 1*1000 microsecond
tks.

Note that you may get overflow when you multiply the value of a 'long' with 1000.

---

### Post by hoboy on 2009-10-19
> **Arndt said:**
> Note that you may get overflow when you multiply the value of a 'long' with 1000.

That is precisely what I have done. what should I have done ?

long calling=System.currentTimeMillis()*1000;

---

### Post by Arndt on 2009-10-19
> **hoboy said:**
> That is precisely what I have done. what should I have done ?

long calling=System.currentTimeMillis()*1000;

One thing I don't know is why you need microseconds in the first place. But there are probably classes that support longer numbers, I'm not that good at Java, Integer or BigInteger or whatever. Or keep the milliseconds as they are, and the microseconds in a separate variable.

---

### Post by Suppermann on 2009-10-19
You can use BigInteger. It's a pain in the *** to use it, tho.

---

### Post by CptPicard on 2009-10-19
I do not understand what the need for the unnecessary extra zeros is though as you're not getting anymore accuracy in the measurement anyway :)

---

