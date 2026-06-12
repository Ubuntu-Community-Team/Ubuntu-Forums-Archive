---
title: "Optimize this common inelegant code"
date: 2010-09-22
forum: Programming Talk
---

### Post by GuillaumeMG on 2010-09-22
f1()
{[INDENT]          if (var == 1)
[/INDENT][INDENT][INDENT]                  f2();
[/INDENT][/INDENT][INDENT]          else if (var == 2)
[/INDENT][INDENT][INDENT]                  f3();
[/INDENT][/INDENT][INDENT]          if (var == 1 || var == 2)
[/INDENT][INDENT][INDENT]                  f4();
[/INDENT][/INDENT][INDENT]          var = 0;
[/INDENT]}

Sometimes, I write some code, look back at it, and say to myself "this could be more elegant". This is the case here, but it's now been 5-10 min and I can neither find a way to render it more elegant nor silence my inner voice saying "this is not optimal". Help?

---

### Post by mikeeve on 2010-09-22
how about adding the f4() after f2() and f3() and just deleting the last "if statement"?

---

### Post by lisati on 2010-09-22
switch?

---

### Post by sisco311 on 2010-09-22
[s]
```
if (var==1 || var==2)
  if (var==1)
    f2()
  else
    f3()
  f4()

```

???[/s]

never mind. mikeeve's suggestion is better.

---

### Post by wkhasintha on 2010-09-23
> **mikeeve said:**
> how about adding the f4() after f2() and f3() and just deleting the last "if statement"?

=D> 

this

---

### Post by Bachstelze on 2010-09-23
The code is just fine as it is IMHO. Changing the order of the functions is just a cosmetic change.

---

### Post by GuillaumeMG on 2010-09-23
Thanks Mikeeve, that's what I was looking for.
> 
The code is just fine as it is IMHO. Changing the order of the functions is just a cosmetic change. 

I agree, that's why I chose the adjective "inelegant". There's some pride one can get from writing elegant code, IMHO.

---

### Post by Bachstelze on 2010-09-23
> **GuillaumeMG said:**
> 
I agree, that's why I chose the adjective "inelegant". There's some pride one can get from writing elegant code, IMHO.

Code elegance is not just a matter of cosmetics, it is also a matter of efficiency by avoiding code duplication, or over-convoluted constructs (even though modern compilers will optimize those away, not all languages are compiled, and they will still hurt readability anyway).

I see no difference in either between your code and sisco311's. In both cases, you have three function calls ant three if clauses. mikeeve's is a trade-off, you eliminate an if-clause, but you have two calls to f4. Also valid, though I personally wouldn't do it.

---

### Post by StephenF on 2010-09-23
> **Bachstelze said:**
> I see no difference in either between your code and sisco311's.
I see that sisco311's fast tracks cases where var is neither 1 or 2.

---

### Post by Bachstelze on 2010-09-23
> **StephenF said:**
> I see that sisco311's fast tracks cases where var is neither 1 or 2.

True, but that's not significant. The fast tracking does not help readability, and has an unsignificant impact on the algorithm's efficiency (you still do two equality tests).

---

### Post by dwhitney67 on 2010-09-23
I would "optimize" away the global variable var, and pass it into f1().  :-)
```

void f1(int* var)
{
   if (*var == 1 || *var == 2) 
   {
      *var == 1 ? f2() : f3();
      f4();
   }

   *var = 0;
}

```
That way, if I ever find myself maintaining the code, I would not have to hunt/peck around as to where was the last instance where the global variable is set before f1() is called.

---

### Post by StephenF on 2010-09-23
> **Bachstelze said:**
> True, but that's not significant. The fast tracking does not help readability, and has an unsignificant impact on the algorithm's efficiency (you still do two equality tests).
If var happened to be four you would be doing four tests. That's twice as many and not something I would want in a tight loop. The only way to be sure would be to look at the assembly output after machine optimisation and that's something that can't be relied on across machines.

---

### Post by worseisworser on 2010-09-23
> **GuillaumeMG said:**
> f1()
{[INDENT]          if (var == 1)
[/INDENT][INDENT][INDENT]                  f2();
[/INDENT][/INDENT][INDENT]          else if (var == 2)
[/INDENT][INDENT][INDENT]                  f3();
[/INDENT][/INDENT][INDENT]          if (var == 1 || var == 2)
[/INDENT][INDENT][INDENT]                  f4();
[/INDENT][/INDENT][INDENT]          var = 0;
[/INDENT]}

Sometimes, I write some code, look back at it, and say to myself "this could be more elegant". This is the case here, but it's now been 5-10 min and I can neither find a way to render it more elegant nor silence my inner voice saying "this is not optimal". Help?

> **mikeeve said:**
> how about adding the f4() after f2() and f3() and just deleting the last "if statement"?

This is the proper solution in this case, but sometimes the call to *f4* might be a lot of code that really doesn't belong in a globally visible function and I then do something like this:

```

CL-USER> (defun f1 (var)
           (flet ((common ()
                    (write-line "common")))
             (declare (inline common))
             (case var
               (1 (write-line "f2") (common))
               (2 (write-line "f3") (common)))))
               
F1

CL-USER> (f1 1)
f2
common

CL-USER> (f1 2)
f3
common

CL-USER> 

```

..i.e., I create an inner or nested function which I might inline so there is no function call overhead either. Perhaps C99 or some GCC extention can do something like this too.

---

### Post by GuillaumeMG on 2010-09-24
> **Bachstelze said:**
> Code elegance is not just a matter of cosmetics, it is also a matter of efficiency by avoiding code duplication, or over-convoluted constructs (even though modern compilers will optimize those away, not all languages are compiled, and they will still hurt readability anyway).

I see no difference in either between your code and sisco311's. In both cases, you have three function calls ant three if clauses. mikeeve's is a trade-off, you eliminate an if-clause, but you have two calls to f4. Also valid, though I personally wouldn't do it.

I'm a relatively new to programming, and I'm still learning to balance code efficacity, readability and maintainability. I like how the thread turned out and I like to hear the opinions of programming veterans. I notice that you are counting function calls and if clauses, I figure this is a way to predict compiled code efficacity, I find it rather interesting.

---

