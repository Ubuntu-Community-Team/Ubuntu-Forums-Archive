---
title: "[C] How do I link this?"
date: 2011-03-19
forum: Programming Talk
---

### Post by raf-kig on 2011-03-19
t1.c```

#include <stdio.h>

int main()
{
    printf("%g\n", val() );
    return 0;
}

```t2.c```
double val() {
  return 65536.0;
}

``````

$ gcc t1.c t2.c
t1.c: In function &#8216;main&#8217;:
t1.c:5: warning: format &#8216;%g&#8217; expects type &#8216;double&#8217;, but argument 2 has type &#8216;int&#8217;

```I know I must be doing something really stupid, so what is it?

Edit: Never mind. I forgot the prototype! I knew it was something stupid.

---

### Post by python3e on 2011-03-19
i also tried to do something similar and faced a similar problem; so i let it be  ...

---

### Post by AbhiJais on 2011-03-20
> **raf-kig said:**
> t1.c```

#include <stdio.h>

int main()
{
    printf("%g\n", val() );
    return 0;
}

```t2.c```
double val() {
  return 65536.0;
}

``````

$ gcc t1.c t2.c
t1.c: In function &#8216;main&#8217;:
t1.c:5: warning: format &#8216;%g&#8217; expects type &#8216;double&#8217;, but argument 2 has type &#8216;int&#8217;

```I know I must be doing something really stupid, so what is it?

Edit: Never mind. I forgot the prototype! I knew it was something stupid.
Surprisingly I tried the same but somehow got different result than yours'. Here is the output.

> bash-4.1$ mkdir development
bash-4.1$ cd development/
bash-4.1$ ls
bash-4.1$ vi t1.c
bash-4.1$ vi t2.c
bash-4.1$ gcc t1.c t2.c
bash-4.1$ ls
a.out  t1.c  t2.c
bash-4.1$ ./a.out
9.58487e-322
bash-4.1$ cat t*.c
t1.c:
#include <stdio.h>

int main()
{
    printf("%g\n", val() );
    return 0;
}
t2.c:
double val() {
  return 65536.0;
}


So what i think is may be there's some different version of compilers we are using. Anyways you can try casting 'val()' explicitely in double and see if the printed vale is int or double.
> 
printf("%g\n", (double)(val()));


P.S. I'm not sure if there is some issue with your machine architecture (32/64 bit).

---

### Post by lucasart on 2011-03-20
> **raf-kig said:**
> t1.c```

#include <stdio.h>

int main()
{
    printf("%g\n", val() );
    return 0;
}

```t2.c```
double val() {
  return 65536.0;
}

``````

$ gcc t1.c t2.c
t1.c: In function &#8216;main&#8217;:
t1.c:5: warning: format &#8216;%g&#8217; expects type &#8216;double&#8217;, but argument 2 has type &#8216;int&#8217;

```I know I must be doing something really stupid, so what is it?

Edit: Never mind. I forgot the prototype! I knew it was something stupid.

You'll keep having these problems so long as you don't understand what compiling and linking actually do.

If you are a beginner to C, which I can see you are, I can only recommend that you work on fhe book of Kerninghan and Ritchie, it exaplains everything you need to know about C and is punctuated by practical examples and exercises. Arguably the best book every written on C (by none other than the inventors of the C language)

[http://cgip.inf.unideb.hu/eng/rtornai/Kernighan_Ritchie_Language_C.pdf](http://cgip.inf.unideb.hu/eng/rtornai/Kernighan_Ritchie_Language_C.pdf)

Hint: When gcc compiles t1.c it has no way of knowing who val() is, so typically it assumes things are int when it doesnt know.. But even if you change the %g you'll get an other error because val() is not defined. The quickest way is to write before the main:

extern double val();

But even cleaner is to write a separate file called t2.h with that line and to #include it (with a #pragma once to avoid recursive inclusion when your program becomes more complex)

---

### Post by trent.josephsen on 2011-03-21
> **lucasart said:**
> You'll keep having these problems so long as you don't understand what compiling and linking actually do.

If you are a beginner to C, which I can see you are, I can only recommend that you work on fhe book of Kerninghan and Ritchie, it exaplains everything you need to know about C and is punctuated by practical examples and exercises. Arguably the best book every written on C (by none other than the inventors of the C language)

[http://cgip.inf.unideb.hu/eng/rtornai/Kernighan_Ritchie_Language_C.pdf](http://cgip.inf.unideb.hu/eng/rtornai/Kernighan_Ritchie_Language_C.pdf)

Hint: When gcc compiles t1.c it has no way of knowing who val() is, so typically it assumes things are int when it doesnt know.. But even if you change the %g you'll get an other error because val() is not defined. The quickest way is to write before the main:

extern double val();

But even cleaner is to write a separate file called t2.h with that line and to #include it (with a #pragma once to avoid recursive inclusion when your program becomes more complex)
Please don't declare functions with extern.

---

