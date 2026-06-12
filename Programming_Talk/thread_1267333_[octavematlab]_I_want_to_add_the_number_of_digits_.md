---
title: "[octave/matlab] I want to add the number of digits in a number"
date: 2009-09-15
forum: Programming Talk
---

### Post by green0eggs on 2009-09-15
Hello!

I'm calculating Fibonacci numbers and I want to count the number of digits for the nth. My code at the moment looks like this:

```
Fn = FnMinus1 + FnMinus2;
DigitCount = columns(isdigit(int2str(Fn))); 
```

Fn being the nth Fib#

My way is fairly longwinded (feel free to skip this paragraph if you know your stuff): 'int2str' converts it to a string, 'isdigit' creates a row vector with 1 for every digit (i.e. 012345678 or 9) in  a different column. Then 'columns' counts the number of columns.

This works fine for 3/4/5 digits but Octave goes dead when I ask it to count 1000 digits. I think it's probably my chain of functions that's slowing me down. Anyone know a better way of doing it?

[It is for a Project Euler problem]("http://projecteuler.net/index.php?section=problems&id=25").

---

### Post by Habbit on 2009-09-15
Simple if you know your basic math, just take ceil(log10(n+1)).

---

### Post by hofsmo on 2009-09-15
Why do you need isdigit? Since you use int2str, the string will only contain whole numbers without any decimals, can't you just use columns directly on the string like this?
```
DigitCount = columns((int2str(Fn));
```

The math solution is probably way faster, and its more elegant.

---

### Post by green0eggs on 2009-09-15
> if you know your basic math

Oh. Apparently I don't. I've never come across that property of log_10 before.

Thanks

---

### Post by green0eggs on 2009-09-15
> can't you just use columns directly on the string like this?

Yes I can. Didn't know that.

Still runs slowly using the string conversions though.

---

