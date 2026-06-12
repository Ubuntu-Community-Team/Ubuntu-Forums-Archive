---
title: "[ANSI C] string manipulation problem"
date: 2009-10-03
forum: Programming Talk
---

### Post by roccivic on 2009-10-03
I would like to append a string to another string. The below code does exactly that, but it places the result in both "str1" and "str2" (for obvious reasons).
Is there any way of accompliscing this task and place the result just in "str2" without affecting "str1"?

Many thanks for any help in advance.

Rouslan

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main (void) {
	char *		str1 = getenv("HOME");
	char *		str2 = strcat(str1, "/foo");

	printf("\nstr1: %s\nstr2: %s\n", str1, str2);

	return 0;	
}
```

---

### Post by MadCow108 on 2009-10-03
```
char * str1="bla";
char str2[100];
snprintf(str2,100,"%s/foo",str1);
```

---

### Post by roccivic on 2009-10-03
Good man yourself,
Thanks

---

