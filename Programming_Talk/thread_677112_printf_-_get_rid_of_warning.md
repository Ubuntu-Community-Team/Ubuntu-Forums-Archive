---
title: "printf - get rid of warning"
date: 2008-01-24
forum: Programming Talk
---

### Post by xlinuks on 2008-01-24
Hi,
when compiling this C code, gcc does compile the code but issues warnings
```

#include <string.h>

main() {
	char str[] = "Hi there\n";
	printf( "%s", str );
}

```
> 
test.c: In function &#8216;main&#8217;:
test.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

Does anyone know how to get rid of them, am i doing something wrong?

Oh nevermind, I had to include <stdio.h>

---

### Post by fyplinux on 2008-01-25
Normally, if you get the message"incompatible implicit declaration of built-in function ‘printf’", you need to #include some external head files, or declare your own functions.

you can get rid of this message by 
```
#include<stdio.h>
```

---

