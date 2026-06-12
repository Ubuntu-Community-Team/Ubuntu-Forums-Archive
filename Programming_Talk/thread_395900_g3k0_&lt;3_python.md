---
title: "g3k0 &lt;3 python"
date: 2007-03-28
forum: Programming Talk
---

### Post by g3k0 on 2007-03-28
Hey guys, I'm pretty new to python but I believe in love at first sight.  If I had started learning it a week earlier the big int program in a contest I was in would have taken two seconds.  And I'm not familiar enough with java to have done it there because I believe its got a big int as well.  I love dynamically typed !!!!! but...
 I was wondering if there is a way to compile the program so that it catches errors then rather than runtime.

---

### Post by pmasiar on 2007-03-28
> **g3k0 said:**
> I was wondering if there is a way to compile the program so that it catches errors then rather than runtime.

You can use PyLint to check your code. Even compile may not check your typing errors (mixing numbers and strings, wrong method, etc). Right Way (tm) to check it is to write tests. Writing tests also forces you to split your functions to testable pieces - improving your API.

Relax. Because you write your dynamic code faster, you have more time left for testing. :-)

---

