---
title: "Algorithm that simplifies a notation"
date: 2012-09-24
forum: Programming Talk
---

### Post by DaviesX on 2012-09-24
About a year ago, I asked this question
[http://ubuntuforums.org/showthread.php?t=1996202](http://ubuntuforums.org/showthread.php?t=1996202)

And the problem was resolved thanks to 11jmb's suggestion of using shunt yard algorithm

But if I can do a constant folding after generating the RPN ?
for example, 
1 + 2*x + 3*x + 3
1 2 x * + 3 x * + 3 +
_00 = 2*3
_01 = 1 + _00
_02 = 3*x
_03 = _01 + _02
_04 = _03 + 3

can it be simplified into
5*x + 4 ?

Thanks

---

### Post by Odexios on 2012-09-24
What's the scope of your project?

While it can be simple (though still not trivial) if you stick with only sums and products of polynomials in only one variable, the difficulty can easily escalate if you plan to consider more complex functions and different variables.

---

### Post by DaviesX on 2012-09-24
I am just curious about how to do that, not a project
Then how is your solution :) ?

---

### Post by xytron on 2012-09-25
> **DaviesX said:**
> I am just curious about how to do that, not a project
Then how is your solution :) ?

This is not going to be so trivial.  This is an example of computer algebra and many of the CAS systems implement a "simplify" command.
  Why don't you just study how they did it.  There are several CAS program that are open source (Axiom, Sage and others).

I'd recommend looking at the source code of [Mathomatic]("http://www.mathomatic.org/math/") it's written in C and it's a command line program so things will be a bit simpler.

Example run;

```


Secure Mathomatic version 16.0.4
Copyright © 1987-2012 George Gesslein II.
200 equation spaces available in RAM; 2 megabytes per equation space.
HTML color mode enabled; manage by typing "help color".
Reading in file specified on the command line...
1&#8722;>  1 + 2*x + 3*x + 3

#1: 4 + (2·x) + (3·x)

1&#8722;> simplify;

#1: 4 + (5·x)

Successfully finished reading script file "/tmp/mserve.LtN25b".
1&#8722;> 
End of input.



```

So download the source and study how he implemented the "simplify" command.

---

### Post by DaviesX on 2012-09-25
Thanks. I'll try that :)

---

