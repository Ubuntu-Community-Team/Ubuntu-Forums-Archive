---
title: "How do interpreters find order of operations?"
date: 2012-04-15
forum: Programming Talk
---

### Post by flyingsliverfin on 2012-04-15
I was wondering how interpreters for languages or even whatever runs on calculators know what to evaluate first according order of operations?
It would have to be something simple so that it's fast and efficient, but I can't really think of anything super simple

---

### Post by satsujinka on 2012-04-16
I'd be willing to bet that for simple calculators, interpretation of input is what takes most of the time. +,-,*,/, and % are probably entirely done in hardware.

If I had to guess, a calculator probably does a pass on the input to convert it into postfix form, which is then easily converted into machine instructions. So probably something like O(n^3) runtime. (two interpretations then the actual run through)

---

### Post by slavik on 2012-04-16
simple calculators do not have an understanding of order precedence. more complicated (scientific) calculators can convert from infix to postfix/prefix (they actually use it to build a tree). converting infix to post/prefix is something that is understood and studied during comp sci course work. usually in a data structures class.

---

### Post by flyingsliverfin on 2012-04-18
> **slavik said:**
> simple calculators do not have an understanding of order precedence. more complicated (scientific) calculators can convert from infix to postfix/prefix (they actually use it to build a tree). converting infix to post/prefix is something that is understood and studied during comp sci course work. usually in a data structures class.

haha actually the prompt i was working on was making an infix to prefix converter... the problem was actually only supposed to work but up to 5 variables (A,B,C...) and only a few operations, but that's boring. My program is pretty slow and doesn't quite work :)

Maybe we'll do something like that in AP comp sci next year (11th grade) but the class is pretty much a joke so probably not :(

---

### Post by bregma on 2012-04-18
> **flyingsliverfin said:**
> haha actually the prompt i was working on was making an infix to prefix converter... the problem was actually only supposed to work but up to 5 variables (A,B,C...) and only a few operations, but that's boring. My program is pretty slow and doesn't quite work :)

Just a hint:  use the *shunting yard algorithm*:  it's O(1), simple and fast.

---

### Post by 11jmb on 2012-04-18
> **bregma said:**
> Just a hint:  use the *shunting yard algorithm*:  it's O(1), simple and fast.

simple and fast, yes, but it's definitely O(n).

---

### Post by bregma on 2012-04-18
> **11jmb said:**
> simple and fast, yes, but it's definitely O(n).
Er, yes, definitely.  I was thinking *O(n^1)*, as opposed to *O(n^2)*, and it just came out of my fingertips wrong.  Polynomial fail.

---

### Post by schauerlich on 2012-04-18
> **satsujinka said:**
> I'd be willing to bet that for simple calculators, interpretation of input is what takes most of the time. +,-,*,/, and % are probably entirely done in hardware.

If I had to guess, a calculator probably does a pass on the input to convert it into postfix form, which is then easily converted into machine instructions. So probably something like O(n^3) runtime. (two interpretations then the actual run through)

That's not O(n^3), that's O(3n) = O(n) - very different.

---

