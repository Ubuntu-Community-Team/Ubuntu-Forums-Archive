---
title: "a c Hair"
date: 2010-09-02
forum: Programming Talk
---

### Post by navaneethan on 2010-09-02
```
main()
{
 printf("%d");
}
```

This gives 0 Here My prediction is Null value is stored at the integer memory allocation Am i correct?

```
main()
{
 printf("%f");
}
```

which doesn't give any output? Here I couldn't able to guess? May you help!!

---

### Post by ibuclaw on 2010-09-02
What you are doing has an **undefined behaviour** - the fact that anything is outputted at all is just by chance...

In the meantime, say hello to -Wall -Werror, and fix your code. ;)

```
gcc -Wall -Werror myapp.c
```

---

### Post by navaneethan on 2010-09-02
yeah these undefined behaviour which responds differently,Here i don't have chance to fix it>Will you?

---

### Post by viralmeme on 2010-09-02
> **navaneethan said:**
> yeah these undefined behaviour which responds differently,Here i don't have chance to fix it>Will you?
```
main()
int i=0;
{
 printf("%d", i);
}
```

---

### Post by nvteighen on 2010-09-02
> **viralmeme said:**
> ```
main()
int i=0;
{
 printf("%d", i);
}
```

Oh my... pre-ANSI C is still alive...

---

### Post by rnerwein on 2010-09-04
> **nvteighen said:**
> Oh my... pre-ANSI C is still alive...
hi 
for sure

main() 
int i = 0;
{
printf("i --> %d\n",i);
}
will cause the following errors:
x.c: In function ‘main’:
x.c:4: error: parameter ‘i’ is initialized
x.c:4: error: declaration for parameter ‘i’ but no such parameter
make: *** [x] Fehler 1

i think better is:
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
int main(int ac,char **av)
{
int i_j = 0; /* that's what it's called a ploish notation ( i is standing for interger ... and ac . for .. f_ for ... ) /*
printf(" value of i_i is: %d\n",i_i);
exit(0);
/* a nother hint is - don't use printf --> it's bufferd ???! */
have fun
ciao

---

### Post by dwhitney67 on 2010-09-04
Polish?  I thought it was Hungarian (notation)?.

In either case, they both are lame and this truth is held in high regard in the s/w industry.

A better choice for a parameter name would be "value", or some other name that actually conveys meaning as to what the hell the variable is used for.

---

