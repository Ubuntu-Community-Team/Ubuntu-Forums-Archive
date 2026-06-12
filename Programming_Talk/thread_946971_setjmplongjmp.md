---
title: "setjmp/longjmp"
date: 2008-10-13
forum: Programming Talk
---

### Post by kachofool on 2008-10-13
How do I use setjmp/longjmp with Ubuntu? (8.04)... I tried man'ing setjmp/longjmp to no avail. I tried to compile the following program but it failed to execute... 

```

#include <iostream>
#include <setjmp.h>

int main(int argc, char** argv)
{
	jmp_buf env;
	int i;
	
	i = setjmp(env);
	printf("i = %d\n", i);
	
  if (i != 0) exit(0);

  longjmp(env, 2);
  printf("Does this line get printed?\n");

}
```


Thanks!

---

### Post by supirman on 2008-10-13
You're using c++ headers (iostream), but using printf, which is in stdio.h.  Also, exit() is from stdlib.h.

Other than that, it's running fine here.  What do you mean by it 'fails to execute'?

```
#include <stdio.h>
#include <stdlib.h>
#include <setjmp.h>

int main(int argc, char** argv)
{
  jmp_buf env;
  int i;

  i = setjmp(env);
  printf("i = %d\n", i);

  if (i != 0) exit(0);

  longjmp(env, 2);
  printf("Does this line get printed?\n");

}


```

```
##(2111:Mon,13 Oct 08$)> gcc setjmp.c

##(2111:Mon,13 Oct 08$)> ./a.out
i = 0
i = 2


```

---

