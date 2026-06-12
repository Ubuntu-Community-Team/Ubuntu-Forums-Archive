---
title: "atoi works, but atof doesn't"
date: 2011-03-20
forum: Programming Talk
---

### Post by layers on 2011-03-20
```
#include <stdio.h>
#include <string.h>

int main(){
char str[80] = "34.3";

float x = atof(&str);

printf("%f \n",x);

return 0;
}
```

\/

```
ibo@ibo-laptop:~/Desktop$ ./a.out
75366.000000 

```

The above is a program, which I works if I do it for int. Why is this not working?

---

### Post by NovaAesa on 2011-03-20
For starters, you shouldn't be passing in the address of str, you should be passing in str itself (remember that arrays can be treated like pointers for the purpose of parameter passing).

I still couldn't get the example to work though... A quick google indicates that atof is deprecated, although I don't think that's the problem.

---

### Post by Arndt on 2011-03-20
> **layers said:**
> ```
#include <stdio.h>
#include <string.h>

int main(){
char str[80] = "34.3";

float x = atof(&str);

printf("%f \n",x);

return 0;
}
```

\/

```
ibo@ibo-laptop:~/Desktop$ ./a.out
75366.000000 

```

The above is a program, which I works if I do it for int. Why is this not working?

Use warnings, and the compiler will tell you:

```
$ gcc -o flo -Wall flo.c
flo.c: In function ‘main’:
flo.c:7: warning: implicit declaration of function ‘atof’
```

The manual page for 'atof' says to include the header file stdlib.h (which is always a good idea to do, don't even think of whether it's needed).

What happens is that when the compiler is not told what 'atof' returns, it has to assume 'int'.

---

### Post by Milliways on 2011-03-20
> **layers said:**
> ```
#include <stdio.h>
#include <string.h>

int main(){
char str[80] = "34.3";

float x = atof(&str);

printf("%f \n",x);

return 0;
}
```
The above is a program, which I works if I do it for int. Why is this not working?

If you 
#include <stdlib.h>
and omit the & before str it should work

---

### Post by trent.josephsen on 2011-03-20
Once you #include <stdlib.h> you should also notice 
```
layers.c: In function &#8216;main&#8217;:
layers.c:7:1: warning: passing argument 1 of &#8216;atof&#8217; from incompatible pointer type
/usr/include/stdlib.h:145:15: note: expected &#8216;const char *&#8217; but argument is of type &#8216;char (*)[80]&#8217;
```

atof(str) is fine.

But you should really use strtod (or, in C99, strtof if you really want a float and not a double).  atof can't detect errors.

---

### Post by layers on 2011-03-20
Just to be consistent with the rest of the program, I included stdlib.h and removed the &. Thank you. They should have included it in the same place where atoi is.

---

### Post by Arndt on 2011-03-20
> **layers said:**
> Just to be consistent with the rest of the program, I included stdlib.h and removed the &. Thank you. They should have included it in the same place where atoi is.

Who's "they"?

I think there is a misconception here that needs to be corrected. If you use 'atoi' and do not include stdlib.h, the compiler gives the same kind of warning for the same reason:

```
$ gcc -o flo -Wall flo.c
flo.c: In function ‘main’:
flo.c:7: warning: implicit declaration of function ‘atoi’

```

---

