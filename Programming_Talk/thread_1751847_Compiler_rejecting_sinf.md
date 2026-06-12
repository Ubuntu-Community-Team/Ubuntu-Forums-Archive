---
title: "Compiler rejecting sinf"
date: 2011-05-07
forum: Programming Talk
---

### Post by AngusH on 2011-05-07
I'm trying to compile the following code just to get a feel for exactly how sinf works, as I need to use it in another piece of code, but the compiler keeps saying it's undefined. Is sinf not defined in math.h?
Program:```
#include "math.h"
#include "stdio.h"

int main()
{
	int h;
	float v;
	v=3.0;
	printf("%f",sinf(v));
	
	return 0;	
}

```
Compiler errors:```
spc1.c: In function ‘main’:
spc1.c:6:6: warning: unused variable ‘h’
/tmp/cc48qBlB.o: In function `main':
spc1.c:(.text+0x1a): undefined reference to `sinf'
collect2: ld returned 1 exit status

```

Thanks in advance everyone. 
Angus

---

### Post by NovaAesa on 2011-05-07
sinf certainly is included in math.h

Have a look at the man page (you might have to install them, they aren't installed by default).
```
man sinf
```
It says in the man page that you have to link with -lm. So you have to compile with something like:

```
gcc -lm -Wall spcl.c
```

---

### Post by AngusH on 2011-05-07
Thanks, it's weird because I swear I've used hypot before without using -lm and it's man page says it requires it too...
Ah well, thanks again for your time.
Angus

---

