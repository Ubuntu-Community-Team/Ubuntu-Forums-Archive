---
title: "[C] Returning a &quot;failed&quot; status from a function"
date: 2010-02-10
forum: Programming Talk
---

### Post by durand on 2010-02-10
Hi,

I'm currently studying C at university and I need to tell the main program that a function has "failed" without making the main program think that the failed status is a returned value.

In python, this is easy. I would just return False instead of the actual return value of the function, however, in C, I can't seem to return something that's not of the type I've defined the function to return. So I'm really confused about what to do...

My simplified code is this:
```

double sqrt_function(a,b) {
    return sqrt(a-b);
}

int main() {
    answer = sqrt_function(a,b);
}

```

I need to tell the main function that the sqrt_function function has failed when a is bigger than b, however, I see no way to do this without the main function interpreting the return value as a proper value...

Ugh, I've only just started C programming and I'm already hating it. Python is way better :p

Thanks!

---

### Post by SaintDanBert on 2010-02-10
What does the C-language library do if you call tan() or sin() or using your example sqrt() and it fails. If you don't know, find out and do the same thing or something similar. *Hint -- Look at math.h.*

Your example calls sqrt() and it could very easily fail as programmed.
How will you know if that happens? What will your code do when it happens? What can your code do and be defensive against these troubles?

The standard run-time-libraries are much better at this than they were not that long ago.

NOTE -- I've taught C-language programming since the early 1980's. Once you discover the answers to the above questions I believe you are on your way to being a much MUCH better programmer.

NOTE -- It is not good netiquette, and might be against forum policy, to ask folks to help you do your homework. This responder believes that I've helped you help yourself by showing you a path to the answers.

Cheers,
~~~ 0;-Dan

---

### Post by durand on 2010-02-10
Thanks for the reply. I've worked out that if the function is invalid, it will produce a nan. I can also return nans using return nan; However, I now have no idea how to catch the nan error and do something. I've tried using nan, NAN, NaN, nan() and nan("") as identifiers but none of them have worked. Here's my test code:

```

#include <math.h>
#include <stdio.h>

double sqrt_function(a,b) {
    return sqrt(a-b);
}

int main() {
    if(sqrt_function(3,4)==NAN)
        printf("NaN!");
}

```
 Whats strange is that I don't get any compile errors so NAN must be right :S

---

### Post by durand on 2010-02-10
Right, I found what I need. isnan(sqrt_function()) does the trick. Thanks.

---

### Post by saulgoode on 2010-02-10
Note that while floating point exceptions are typically disabled by GCC on GNU/Linux platforms, the same may not be true for other targets (and some installations of GNU/Linux may enable them).

To avoid generating floating point exceptions (SIGFPE), I would recommend you test for negative values before taking the square, but still use NAN as a flag for the error condition:

```
double sqrt_function(double a, double b) {
  if (a < b) 
    return NAN;
  else
    return sqrt(a - b);
  }
```

To enable the NAN macro, you may have to define the following constant *before* including <math.h>.

**#define __USE_ISOC99**

---

### Post by MadCow108 on 2010-02-11
this is over the top for this problem but you can also throw exceptions in C with the jump functions
[http://www.cplusplus.com/reference/clibrary/csetjmp/](http://www.cplusplus.com/reference/clibrary/csetjmp/)

but their difficult to handle

also there is another easy way (and probably what SaintDanBert meant)
check: man sqrt

---

### Post by durand on 2010-02-11
Hmm, ok. I'll have to keep both suggestions in mind. Whats the NAN macro?
Thanks!

---

