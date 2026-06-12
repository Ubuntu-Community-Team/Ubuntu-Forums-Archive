---
title: "Regex noob question"
date: 2009-09-25
forum: Programming Talk
---

### Post by pylon42 on 2009-09-25
Hello!

I'm trying to learn some Regex... I've taken a few tutorials so far today and everything is working well and makes sense. I just have one question:

Is there some kind of "&" operator that I'm not seeing?

For example:

a|b returns every line with 'a' OR 'b'. What if I want every line with 'a' AND 'b'? (not 'ab').

?
Thanks in advance.

---

### Post by geirha on 2009-09-25
There's no AND operator that I know of, so you haven't missed it ... or we've both missed it ;) Typically, you'll use something like "a.*b" if you know that a will come before b. If you don't know the order, you'd do "a.*b|b.*a". Another option is to match lines containing a, then do a substring match for b (without using regex) afterwards.

Usually, when you want to look for both a and b, you want them in only one order.

---

### Post by myrtle1908 on 2009-09-25
Or you could AND a couple of expressions together eg

```
use strict;
use warnings;

while (<DATA>) {
   print if /a/ && /b/;
}

__DATA__
this line contains a and b
this line contains a only
```

---

### Post by pylon42 on 2009-09-25
Thank you both - the replies were extremely helpful :)

---

