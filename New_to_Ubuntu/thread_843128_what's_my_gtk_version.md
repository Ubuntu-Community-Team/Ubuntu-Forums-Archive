---
title: "what's my gtk version?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-28
how do you find out which version of gtk you are running?

---

### Post by stig on 2008-06-28
I hope you get an answer because I would like to be able to check what my version is. I looked for GTK in Synaptic but it doesn't seem to give the version of what is installed other than GTK 2.x

Firefox 3 apparently needs GTK 2.10 or greater and I think mine is lower than that (I'm using Dapper). So I ned to be able to find out what my version is.

Also, for a non-techie like me, the numbering of versions of software seems wierd. Mathematically, 2.8 is greater than 2.10, but in software it looks like 2.10 is above 2.8. How did that come to be accepted? :(

---

### Post by mcduck on 2008-06-28
> **stig said:**
> 
Also, for a non-techie like me, the numbering of versions of software seems wierd. Mathematically, 2.8 is greater than 2.10, but in software it looks like 2.10 is above 2.8. How did that come to be accepted? :(

How come? It's not two-point-eight and two-point-one-zero. the numbers after the dot are 8 and 10, and 10 sure is bigger number than eight is.. They are version numbers, not decimals.

---

### Post by bubba_169 on 2008-06-28
In a termainal:

```
dpkg -l | grep libgtk
```

It might be easier to copy and paste to make sure you get the '|' character correct... :D
I think the one you need is the libgtk2.0-bin - it will tell you the version number straight after.

Quick tip, its easier to read this in a larger terminal window ... possibly maximized

---

### Post by leemajors on 2008-06-28
many thanks, that did the trick. now i need to learn how to retain that sort of information!!!

---

### Post by niteshifter on 2008-06-28
Hi,

> Also, for a non-techie like me, the numbering of versions of software seems wierd. Mathematically, 2.8 is greater than 2.10, but in software it looks like 2.10 is above 2.8. How did that come to be accepted?

That's because the count of versioning schemes for code is approximately equal to the count of people producing code. Further, one's own scheme makes sense in a (pick at least one):

A) Logical
B) Intuitive
C) Mathematical
D) Common Sense
E) Ordered / Orderly

way, everybody else's is just dumb ;)

---

