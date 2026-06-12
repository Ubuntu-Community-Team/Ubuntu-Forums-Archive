---
title: "C question"
date: 2008-06-08
forum: Programming Talk
---

### Post by dmm1285 on 2008-06-08
In a program I am working on, I put this on accident:
 float *coefficients = malloc(number_coefficients*sizeof(float));
instead of this:
 float *coefficients = (float *) malloc(number_coefficients*sizeof(float));
The program seems to work fine. Was I lucky that it worked, or is there some kind of implicit casting going on that makes the first version acceptable?

---

### Post by LoneWolfJack on 2008-06-08
malloc returns a void pointer, so you should not typecast malloc in C... C++, however, will throw an error without a typecast.

---

### Post by dmm1285 on 2008-06-08
> **LoneWolfJack said:**
> malloc returns a void pointer, so you should not typecast malloc in C... C++, however, will throw an error without a typecast.

Thanks. I just looked at the wikipedia page for malloc (which I should have looked at first) and it says that malloc used to return *char and so an explicit cast used to be necessary.

---

### Post by dmm1285 on 2008-06-08
Another question:

According to [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1047673478](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1047673478), the preferred way to use malloc is:
double *p;
p = malloc ( n * sizeof *p );

Would this always be safe:
double *p = malloc ( n * sizeof *p );

or could using the pointer in its assignment statement cause problems? I just tried it out and it seemed to work ok, but logically it would seem to cause a problem.

---

### Post by dwhitney67 on 2008-06-09
> **dmm1285 said:**
> Another question:

According to [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1047673478](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?id=1043284351&answer=1047673478), the preferred way to use malloc is:
double *p;
p = malloc ( n * sizeof *p );

Would this always be safe:
double *p = malloc ( n * sizeof *p );

or could using the pointer in its assignment statement cause problems? I just tried it out and it seemed to work ok, but logically it would seem to cause a problem.
The second way you have listed is my preferred way to initialize a local variable.  And yes, it is safe.  For the sake of readability, I would recommend that the *p be placed between parenthesis.

Like:
[PHP]double *p = malloc( n * sizeof(*p) );[/PHP]

---

