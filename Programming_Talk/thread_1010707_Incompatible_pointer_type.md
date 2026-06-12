---
title: "Incompatible pointer type"
date: 2008-12-14
forum: Programming Talk
---

### Post by slushpuppy on 2008-12-14
```
#include <stdio.h>
#include <stdlib.h>
	

int main (int argc, char *argv[]) {
	char **pointer,*p;
	int i = 0;
	pointer = malloc(9);
	while (i <= 8) {
		pointer[i] = malloc(31);
		pointer[i] = "hello";
		i++;
	}
	 printf("%s\n",pointer[0]);
	 pointer = realloc(pointer,30);
	 while (i <= 19) {
		 pointer[i] = malloc(31);
		 pointer[i] = "hellllllooo";
		 i++;
	 }
}


```
The output message is a memory dump. I am compiling using gcc and the command $ gcc test.c. Thanks!

---

### Post by Bachstelze on 2008-12-14
Replace

```
        pointer = malloc(9);
```

with

```
        pointer = malloc(9*sizeof(char*));
```

Or better yet:

```
        pointer = calloc(9, sizeof(char*));
```

---

### Post by slushpuppy on 2008-12-14
> **HymnToLife said:**
> Replace

```
        pointer = malloc(9);
```

with

```
        pointer = malloc(9*sizeof(char*));
```

Or better yet:

```
        pointer = calloc(9, sizeof(char*));
```

Hi, thanks. Could you kindly explain the significant of using the sizeof of a char pointer?

---

### Post by Bachstelze on 2008-12-14
```
firas@nobue ~ % cat test.c
#include <stdio.h>

int main(void)
{
        printf("%lu\n", sizeof(char*));
        return 0;
}
firas@nobue ~ % cc -o test test.c
firas@nobue ~ % ./test
8

```

The size of a [FONT="Courier New"]char*[/FONT] is thus 8 bytes. Therefore, if you do [FONT="Courier New"]pointer = malloc(9)[/FONT], [FONT="Courier New"]pointer[/FONT] will not be allocated enough memory to hold all the data you will put in it.

---

### Post by slushpuppy on 2008-12-14
> **HymnToLife said:**
> ```
firas@nobue ~ % cat test.c
#include <stdio.h>

int main(void)
{
        printf("%lu\n", sizeof(char*));
        return 0;
}
firas@nobue ~ % cc -o test test.c
firas@nobue ~ % ./test
8

```

The size of a [FONT="Courier New"]char*[/FONT] is thus 8 bytes. Therefore, if you do [FONT="Courier New"]pointer = malloc(9)[/FONT], [FONT="Courier New"]pointer[/FONT] will not be allocated enough memory to hold all the data you will put in it.
Thanks!

---

