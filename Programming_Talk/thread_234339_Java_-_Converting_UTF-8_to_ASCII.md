---
title: "Java - Converting UTF-8 to ASCII"
date: 2006-08-11
forum: Programming Talk
---

### Post by MrHorus on 2006-08-11
Hi, got a little problem I need some advice with.

I have a USB GPS device that I am reading from and the data appears to be UTF-8 encoded.

When I have a look at this and print it then it appears to be a list of numbers, presumbly each number corrosponds to an ASCII or Unicode char.

Now, is there an easy method or simple way to decode this and just get the English/Latin-1 chars?

---

### Post by yaaarrrgg on 2006-08-15
Java supports reading and writing UTF-8 strings through InputStreamReader and OutputStreamWriter (the charset can be set in the constructor).

Although, why do you think it is UTF-8?  It could very easily be a proprietary binary format.

---

