---
title: "factoring a 60 digit number"
date: 2009-03-20
forum: Programming Talk
---

### Post by Marco A on 2009-03-20
.

---

### Post by jespdj on 2009-03-20
> **Marco A said:**
> I was wondering if someone could please try to factor that integer, I know for certain that it is composite.
That's not very hard to see, it's an even number so ofcourse it's composite.

---

### Post by monkeyking on 2009-03-20
These are the factor and their exponents
{{2, 2}, {19, 1}, {37, 1}, {53, 1}, {971, 1}, {1462113599, 
  1}, {1674876024766645930034956651962022197358141, 1}}

I didn't bother to check,
because I never make errors or bugs in my programs :)

I just copy pastied you number again
and now it gives me
{{2, 2}, {3, 1}, {141871131616823747871637573, 
  1}, {355924440886501016678474443973521, 1}}

I Think the last one is the correct one,
since I think I might have accidently deleted a digit the first time.

---

### Post by Marco A on 2009-03-20
.

---

### Post by kjohansen on 2009-03-20
I confirm the above answer.  This website does it in a few seconds with the elliptocal method:
[http://www.alpertron.com.ar/ECM.HTM](http://www.alpertron.com.ar/ECM.HTM)

---

### Post by monkeyking on 2009-03-20
Actually I just started mathematica and typed
[PHP]
FactorInteger[60594483838383827346664448848484848484877333228949 5848454396][/PHP]

So not a big deal.
It took more than 1. minut but less then 5.
Its an 6 year old laptop with 1.256 gig mem.
And I was browsing the web, watching tvshows and all that while it was calculating.

Some parts of mathematica is build on gmp, I have no idea which parts.
But I'm quite confident that it should be done in less than 10 minutes for something not optimized.

I haven't used gmp for some time,
but it has the roland method
[http://www.srcdoc.com/gmp_4.1.4/factorize_8c.html#a4](http://www.srcdoc.com/gmp_4.1.4/factorize_8c.html#a4)

But are you trying to implement your own version?

---

### Post by Paul Miller on 2009-03-24
You should look into the [general number field sieve]("http://en.wikipedia.org/wiki/General_number_field_sieve").

BTW, factoring your number took me 99 seconds using Mathematica on my 1.7 Ghz dual-core Athlon laptop.

---

### Post by Marco A on 2009-03-25
.

---

