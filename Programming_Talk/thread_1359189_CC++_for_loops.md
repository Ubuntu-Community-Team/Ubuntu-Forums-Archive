---
title: "C/C++ for loops"
date: 2009-12-19
forum: Programming Talk
---

### Post by Hetepeperfan on 2009-12-19
Recently I accidentally wrote the for loop

```
for (i = 0; i = 100; i++)
```This should have been 

```
for (i =0; i <= 100; i++)
```I noticed that the first loop kept looping for a long long while...
But I do not understand why. Can someone please explain me why the first one keeps looping forever.

regards hetepeperfan

---

### Post by PmDematagoda on 2009-12-19
You are simply assigning a value to the variable i, not checking if the condition is true(which was probably your intention), hence the "condition" always evaluates to true(since there is a value) and the loop keeps going. If you printed the variable i, it would probably go like this:-
```
100
100
100
...
```

---

### Post by Hetepeperfan on 2009-12-19
Thanks that makes my understanding more clear :)

---

### Post by lightstream on 2009-12-19
The for loop is equivalent to a while loop, in your case it would be the following statements:

```

int i;
i = 0;
while (i = 100) {
  ...
  i++;
}
```

---

### Post by SledgeHammer_999 on 2009-12-19
And since noone has mentioned it the correct thing would be:
```
for (i = 0; i == 100; i++)
```

Well not correct, the loop would never run in this case...

---

### Post by wmcbrine on 2009-12-19
```
for (*initialization*; *condition*; *increment*)
```

You can actually put *any expression* into each of the three positions -- the usual form is just a convention, and you'll often see loops that deviate from it. As lightstream says, the above logically translates *exactly* to:

```
*initialization*;
while (*condition*) {
    ...
    *increment*;
}
```

although the compiler may or may not output the same code for both, due to optimization.

In this case, "i = 100" evaluates to 100, which evaluates to True. It also sets i to 100, of course (over and over), but that's not the important bit as far as the loop is concerned.

BTW, PmDematagoda is not quite correct to say "since there is a value". Had you written "i = 0" for the condition, that expression would evaluate to False, and the body of the loop would never execute.

---

### Post by quip on 2009-12-19
> **lightstream said:**
> The for loop is equivalent to a while loop, in your case it would be the following statements:

```

int i;
i = 0;
while (i = 100) {
  ...
  i++;
}
```

You also neglected to correct the syntax flaw itself while pointing out the problem of testing for equality to 100; namely, that ```
=
``` is not the same as ```
==
```

Your while condition should be ```
while (i **==** 100)
```, which is still not what the OP wanted, but is the operator that he needs to use to test for equality.

---

### Post by dwhitney67 on 2009-12-19
I'm curious... when someone, such as PmDematagoda, gives the correct response to the OP's question, and then the OP is satisfied with the response, why is it necessary for others to regurgitate the same response over and over again?

Oh well... at least everybody was spot on with their responses.

---

### Post by lightstream on 2009-12-19
> **dwhitney67 said:**
> I'm curious... when someone, such as PmDematagoda, gives the correct response to the OP's question, and then the OP is satisfied with the response, why is it necessary for others to regurgitate the same response over and over again?

Oh well... at least everybody was spot on with their responses.

the same reason you posted the above -- because we're all incorrigible smart arses!

---

### Post by Some Penguin on 2009-12-19
If you're using gcc, this sort of thing will be flagged as a warning if you use -Wall.  It's *legal*, but is something that is usually unintentional and therefore somewhat worthy of remark.

One practice that will also cut down the risk of doing so at the cost of making your code look slightly weirder is putting the constant on the left.  e.g.

for (i=0; 100 = i; i++) {
}

would have generated errors,  not warnings, because it's illegal to use a constant as an lvalue (destination of assignment).   This isn't that useful for loop variables where you tend to be using < or > (possibly in conjunction with =), but it might help you with null comparisons -- e.g.

if  (NULL == foo) {
}

If you carelessly use '=' instead of '==', the compiler will rightfully balk and tell you that you messed up (error, not warning).  If you reversed the order and messed up in the same way (foo = NULL), you just overwrote a variable with NULL and have a constant comparison that depends on the value of NULL.

---

### Post by quip on 2009-12-19
> **lightstream said:**
> the same reason you posted the above -- because we're all incorrigible smart arses!

Exactly! 

@dwhitney67:  Isn't that why you took the time to lengthen the thread by asking the question?  :p

---

### Post by dwhitney67 on 2009-12-19
> **quip said:**
> Exactly! 

@dwhitney67:  Isn't that why you took the time to lengthen the thread by asking the question?  :p

No. I lengthened the thread because I found it annoying to find 10 (perhaps an exaggeration) different spins of the same answer as given by PmDematagoda.

If this is the lame entertainment value that the UF folks want, then damn, let's just throw some more crap into the mix.  The proper format for C++ is...
```

for (int i = 0; i <= 100; ++i)
{
   ...
}

```
Note how I meticulously initialized the variable 'i' within the initialization portion of the for-loop... wow!

Also, note that I used pre-increment versus post-increment.  Ooooh!

This also works for C, if one compiles with GCC's implementation of the ISO 1999 C standard.  This can be invoked using the GCC option -std=c99 or -std=gnu99.

By now, hopefully I have extracted a chuckle or two with my response.

---

### Post by nvteighen on 2009-12-20
> **dwhitney67 said:**
> No. I lengthened the thread because I found it annoying to find 10 (perhaps an exaggeration) different spins of the same answer as given by PmDematagoda.

If this is the lame entertainment value that the UF folks want, then damn, let's just throw some more crap into the mix.  The proper format for C++ is...
```

for (int i = 0; i <= 100; ++i)
{
   ...
}

```


And don't forget that in Common Lisp, you do this using the all-powerful loop macro:
```

(loop for x to 100
      do ...)

```

---

### Post by grayrainbow on 2009-12-20
> **lightstream said:**
> the same reason you posted the above -- because we're all incorrigible smart arses!
It has its benefits sometimes...I guess :o :D

---

### Post by Spiritof76 on 2009-12-20
When someone asks a question there might be a bunch of folks who  have the same question.
An answer is good, a discussion with some analysis is even better..

---

