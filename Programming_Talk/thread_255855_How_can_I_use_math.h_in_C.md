---
title: "How can I use math.h in C?"
date: 2006-09-12
forum: Programming Talk
---

### Post by Lster on 2006-09-12
Some code I have made gives me an error because it cant find sqrt and floor. I thought they were included in math.h. It works with g++, but I would prefer to use gcc.

Thanks all

---

### Post by amo-ej1 on 2006-09-12
* First you're missing a ; after your printf()
* Second: 
when you read the manpage (man sqrt) you'll see

```

NAME
       sqrt, sqrtf, sqrtl - square root function

SYNOPSIS
       #include <math.h>

       double sqrt(double x);
       float sqrtf(float x);
       long double sqrtl(long double x);

       Link with -lm.

```

So your solution is

```

gcc -lm file.c

```

(oh and using [code] tags will preserve your identation)

---

### Post by Lster on 2006-09-12
Wow... Thankyou soooo much :-D

---

