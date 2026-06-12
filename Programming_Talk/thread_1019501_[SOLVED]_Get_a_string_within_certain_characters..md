---
title: "[SOLVED] Get a string within certain characters."
date: 2008-12-23
forum: Programming Talk
---

### Post by ratmandall on 2008-12-23
I need a method to do whats in the link below, except in python, I am assuming it isn't that hard.

[http://www.dreamincode.net/forums/showtopic30009.htm](http://www.dreamincode.net/forums/showtopic30009.htm)

Thanks in advanced.

---

### Post by mike_g on 2008-12-23
If you are dealing with XML you might find a library useful. I havent used this myself, but you could check [this](http://www.chilkatsoft.com/python-xml.asp) out.

---

### Post by ratmandall on 2008-12-23
> **mike_g said:**
> If you are dealing with XML you might find a library useful. I havent used this myself, but you could check [this](http://www.chilkatsoft.com/python-xml.asp) out.

No I am just dealing with a string.
Eg,"Id=212323&"
Pull out what ever is within "Id=" and "&"

---

### Post by escapee on 2008-12-23
> **ratmandall said:**
> I need a method to do whats in the link below, except in python, I am assuming it isn't that hard.


Take a look at regular expressions (REGEX) if you'd like to do it simply and don't know what's between the 'Id=' and the '&', but both of those substrings are always there.

---

### Post by ghostdog74 on 2008-12-23
> **ratmandall said:**
> No I am just dealing with a string.
Eg,"Id=212323&"
Pull out what ever is within "Id=" and "&"

i am not going to do it for you as its very easy. you can use split() to on "=" and then strip() to strip out the "&". Or if you are certain the "&" will definitely be the last character, you can use index slicing.

---

### Post by ratmandall on 2008-12-24
> **ghostdog74 said:**
> i am not going to do it for you as its very easy. you can use split() to on "=" and then strip() to strip out the "&". Or if you are certain the "&" will definitely be the last character, you can use index slicing.

:guitar: :)
Thanks, it works for what I need, and will be handy in the future.

---

