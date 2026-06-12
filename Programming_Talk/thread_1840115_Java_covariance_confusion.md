---
title: "Java covariance confusion"
date: 2011-09-07
forum: Programming Talk
---

### Post by WinterMadness on 2011-09-07
Im taking an algorithms/d.s class and im a bit confused on this topic. My book has a section about compatible array types, and mentions covariance, but does not really explain what it is or what it means. I looked at wikipedia and some other sites, but it got a little over my head. I was wondering if someone here can explain it in simple terms?

what is it?
how does knowing about it help solve problems?

---

### Post by 1clue on 2011-09-07
It's not complicated.

Let's say you have a **long** variable and want to convert it to an **int**.  That's covariance.

Contravariance is when you have an **int** and you want to make it into a **long**.

---

### Post by 1clue on 2011-09-07
Sorry, I guess I neglected to read the last sentence.

When you're converting between types there is almost always a certain amount of processing that occurs, and that has a sort of overhead.  Usually that is negligible but if you're doing something intensive and using every resource at its capacity that overhead can cause delays.

As well, some data types might not have an exact analog for every possible value in the destination type even if it's a larger version of the same basic type.

Going the other direction with contravariance, you need to understand that if the value of the source has more precision than the destination data type can offer, you will either lose some precision or you will throw an error.  You also need to understand where the precision will be lost.

Let's say you have a database.  One column is varchar(100) and another is varchar(50).  Most data probably will fit right in, but if the value in column A has 75 characters then in most text-based schemes you would truncate the last 25 characters off the string, but in some cases you might want to do some other manipulation.

In the event of a Double going to a float, you might lose precision toward the least significant characters, basically losing a number of digits of precision.  Or if the numbers are very large then you might instead lose the ability to hold the exponent.  In other words, a floating point can overflow or underflow in either the exponent or the base.

If you lose track of that sort of thing, you can have inexplicable errors in your code.

---

### Post by 1clue on 2011-09-07
Part of designing software is deciding how important your error conditions are and what you should do about it.

What happens if you coerce a value from a large data type to a small one and the value doesn't fit?  Do you lose a trillionth of a penny, or does the plane crash?

What do you do about each type of error?  What response is least likely to cause the plane to crash?  You can't even begin to address that sort of question if you don't know what sort of problems arise from each type of data conversion.

---

### Post by ofnuts on 2011-09-07
> **1clue said:**
> Part of designing software is deciding how important your error conditions are and what you should do about it.

What happens if you coerce a value from a large data type to a small one and the value doesn't fit?  Do you lose a trillionth of a penny, or does the plane crash?
I have worked with banks and they would much prefer the plane to crash :)

---

