---
title: "C Function that returns a function"
date: 2009-01-25
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-25
I recently found out that it is possible to define a function inside another function. But is is possible to return that inside function as a pointer. Similar to passing a function pointer as an argument. Like Lambda expressins in Lisp's.

---

### Post by slavik on 2009-01-25
return the void *

---

### Post by Mr.Macdonald on 2009-01-25
cool, I can do hacked up lambda calculus in C

---

### Post by CptPicard on 2009-01-25
I don't understand... C does not allow you to return lambda expressions. The GCC extension of nested function specifically produces "weird" results if you return the nested function's pointer after the stack frame has been removed. C does not have frames independent of stack, and this is why you can't have closures associated to lambda expressions, which are the other side of the coin... you can choose a function at runtime, but the environment is what you'll be missing.

---

### Post by Mr.Macdonald on 2009-01-25
I found that if you return a function, then that function can be run only once, until all the scopes are destroyed. And stack variables are destroyed.

try this code,
```
#include <stdio.h>
#include <stdlib.h>

void* funcget(int * a) {
	int addone(int b) {
		return b+(*a);
	}
	return &addone;
}

int main(void) {
	int (*addone)(int);
	int * a = malloc(sizeof(int));
	*a = 2;
	
	
	addone = funcget(a);
	
	printf("%d\n", addone(2));
	printf("%d\n", addone(2));
	
	free(a);
	return 0;
}

```

---

### Post by CptPicard on 2009-01-25
It's interesting enough that you can run it once, I would not have given you even that... :) but yeah, here's one core semantic difference between languages like C and higher-level languages -- your nested functions are "bound to the stack" and there is no way around that no matter how much library you tried writing, unless you really start writing a higher-level language itself.

---

