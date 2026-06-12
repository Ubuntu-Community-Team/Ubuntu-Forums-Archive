---
title: "URL encoding"
date: 2011-01-05
forum: Programming Talk
---

### Post by yc2 on 2011-01-05
Hi,

I am sending get-arguments in the URL string. I have done this before but today I seem to have mental block. ;)

This link
```
<a href="http://example.com/list_hits_new.php?not_bot=1&not_mine=1&dis=1&lim=40">list_hits_new</a>
```

will redirect to this url (IE and Chrome)
```
http://example.com/list_hits_new.php?not_bot=1¬_mine=1&dis=1&lim=40

```
It seems the combination
&not
gives a graphics character! It looks a little like a minus (indicating not). How should I break this pattern. (I cannot encode the n in not (%6E), I tried that.) (The reference encoding for ¬ is %AC)

I assume &not is HTML encoding, interfering.

It works OK (at least as I expect it to) in FF. (the arguments not_bot and not_mine are passed on correctly, but I get the graphics character in Chrome and IE and of course the program then receives incorrect arguments.)

I am probably tired but I can't make it work. Please tell me how to fix it.

Thanks

---

### Post by odyniec on 2011-01-05
> **yc2 said:**
> ```
<a href="http://example.com/list_hits_new.php?not_bot=1&not_mine=1&dis=1&lim=40">list_hits_new</a>
```

Replace each "&" with "&amp;".

(Explanation: [http://htmlhelp.com/tools/validator/problems.html#amp](http://htmlhelp.com/tools/validator/problems.html#amp))

---

### Post by yc2 on 2011-01-05
Aahh, that was it!

Thanks odyniec.

Thread solved.

---

