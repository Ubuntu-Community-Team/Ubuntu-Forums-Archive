---
title: "[BASH] What does the variable ${1-.} contain?"
date: 2014-04-11
forum: Programming Talk
---

### Post by sha1sum on 2014-04-11
Dear forum members,

I was reading through a bash script of one of my coworkers, and I see that he uses the variable ${1-.}. When I echo it in the ternimal, it simply returns 
```
$ echo ${1-.}
.
```

It looks like it does the same thing as $PWD

My question is: Is there a difference between using ${1-.} and $PWD in a script?

---

### Post by sisco311 on 2014-04-11
$1 expands to the first positional parameter. ${1-.} is a parameter expansion: If the first positional parameter is unset then `.' is substituted.


See:[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)
and from the manual:
```
man bash | less +/"Parameter Expansion"
```

---

### Post by sha1sum on 2014-04-11
I get it. Thanks!

---

### Post by sha1sum on 2014-04-11
One quick follow-up question:

Is there a difference between ${1-.} and ${1:-.} ?

Or in general between

```
${var:-value}
```
and
```
${var-value}
```

---

### Post by ofnuts on 2014-04-11
From [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

> 
Omitting the colon results in a test only for a parameter that is unset. Put another way, if the colon is included, the operator tests for both parameter&#8217;s existence and that its value is not null; if the colon is omitted, the operator tests only for existence.


---

### Post by sha1sum on 2014-04-12
Thanks! You guys rock. :guitar:

---

