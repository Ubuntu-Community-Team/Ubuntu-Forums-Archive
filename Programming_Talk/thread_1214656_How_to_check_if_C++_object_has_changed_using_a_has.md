---
title: "How to check if C++ object has changed using a hash"
date: 2009-07-16
forum: Programming Talk
---

### Post by bluedalmatian on 2009-07-16
I was wondering what the best way of checking if a particular C++ object has had any of its attributes altered.

My inital thoughts were to compare MD5 hashes, but I dont think this is guaranteed to always produce different hashes if the object has changed.

Any suggestions welcome

Thanks

---

### Post by Sockerdrickan on 2009-07-16
have a member that holds a time() value when it was edited the last time? or do you mean outside of the class, maybe some memcmp of a copy of the vector with all instances from last check, and the current ones.

---

### Post by lisati on 2009-07-16
The idea has some merit.

I'm not sure how easily it can be adapted, but a few years back I came across a utility "CRCSET" that would allow a C program for MS-DOS or Windows incorporate self-checking code that would let the program know if it had been tampered with (e.g. by a malware). More info (and code snippets) can be found at [http://www.programmersheaven.com/download/3113/download.aspx](http://www.programmersheaven.com/download/3113/download.aspx)

---

### Post by Zugzwang on 2009-07-16
> **bluedalmatian said:**
> My inital thoughts were to compare MD5 hashes, but I dont think this is guaranteed to always produce different hashes if the object has changed.


Any function that maps a finite domain onto a finite domain that is smaller will have the property that there are two objects that map to the same value (due to the pidgeon-hole principle). However, it is extremely hard to get two objects that are mapped to the same value with MD5, so this approach works quite well.

In fact, if the probability of unnoticed changes during the run of your program is smaller than the probability of your computer getting broken within the next 20 years (as an example), then that function should be relatively safe to use.

---

