---
title: "Don't understand why this won't work (Pointers, C)"
date: 2009-09-21
forum: Programming Talk
---

### Post by tom66 on 2009-09-21
```

/* examples */
#include <stdio.h>
#include <string.h>

typedef struct State _State;
struct State {
	int money, bet;
};

int main()
{
	_State *st;
	st->money = 0;
	
	printf("struct size: %d, ptr: %d, st->money: %d\n", sizeof(_State), &st, st->money);
	//memset(st, 0, sizeof(_State));
}

```

The above code has a Segmentation Fault. What am I doing wrong?

---

### Post by dwhitney67 on 2009-09-21
You have declared a local parameter, st, which is a pointer to someplace in memory.  You have yet to assign it a valid location (of memory).

You probably want to allocate (although this is not necessary!) a location in memory.  Here's how:
```

#include <stdlib.h>

...

_State* st = malloc(sizeof(_State));   /* allocate memory from the heap */

st->money = 0;

...

free(st);   /* deallocate memory */

```

Alternatively, if you want to declare a local variable of type _State, you would do something similar to the following:
```

_State st;    /* notice, the st object is declared on the stack! */

st.money = 0;

...

```

---

### Post by Arndt on 2009-09-21
> **dwhitney67 said:**
> You have declared a local parameter, st, which is a pointer to someplace in memory.  You have yet to assign it a valid location (of memory).

You probably want to allocate (although this is not necessary!) a location in memory.  Here's how:
```

#include <stdlib.h>

...

_State* st = malloc(sizeof(_State));   /* allocate memory from the heap */

st->money = 0;

...

free(st);   /* deallocate memory */

```




Don't forget to check the result from 'malloc'. It may be NULL, indicating that the allocation failed. (What your program is supposed to do then is up to you.)

---

### Post by tom66 on 2009-09-21
The thing is, I've always been able to create int* pointers and work with them directly without assigning them an address, it seems like the runtime does this automatically...

```

#include <stdio.h>

int main()
{
	int *i;
	i = 53;
	printf("%d, %d\n", i, &i);
}

```

Output: 53, -1079642224

Am I going about this the wrong way??

---

### Post by Arndt on 2009-09-21
> **tom66 said:**
> The thing is, I've always been able to create int* pointers and work with them directly without assigning them an address, it seems like the runtime does this automatically...

```

#include <stdio.h>

int main()
{
	int *i;
	i = 53;
	printf("%d, %d\n", i, &i);
}

```

Output: 53, -1079642224

Am I going about this the wrong way??

This code snippet actually does nothing. What are you going to use i for? If you ever dereference it, that is, use the place where it is pointing (byte 53 in memory) for reading or storing, the program will probably crash. If you don't dereference it, you may as well use the type 'int', rather than 'int *'.

What happened automatically here was that i itself got an address (on the stack). But i wasn't assigned anything itself automatically - you did that, setting it to 53.

---

### Post by dwhitney67 on 2009-09-21
tom66, the reason your sample app worked is due to shear luck.  The int pointer is uninitialized, and the fact that it points to some place within your program space was mere coincidence.  Because of this coincidence, you were able to assign a value (53) within the location pointed to be the pointer.

In conclusion, you are incorrect in your assumptions.  Learn/understand how malloc() and calloc() work for allocating memory, and of course free() for de-allocating memory.

---

### Post by SledgeHammer_999 on 2009-09-21
> **tom66 said:**
> The thing is, I've always been able to create int* pointers and work with them directly without assigning them an address, it seems like the runtime does this automatically...

```

#include <stdio.h>

int main()
{
	int *i;
	i = 53;
	printf("%d, %d\n", i, &i);
}

```

Output: 53, -1079642224

Am I going about this the wrong way??

Yes you are. You ARE assigning it an adress. You point i to address 53. If address 53 is used by something else in your program and you change it's contents through i then it will result in strange behavior(propably it will crash).

&i returns a pointer to your pointer. To dereference the pointer i you should use ***i** NOT **&i**

---

### Post by Arndt on 2009-09-21
> **dwhitney67 said:**
> tom66, the reason your sample app worked is due to shear luck.  The int pointer is uninitialized, and the fact that it points to some place within your program space was mere coincidence.  Because of this coincidence, you were able to assign a value (53) within the location pointed to be the pointer.

In conclusion, you are incorrect in your assumptions.  Learn/understand how malloc() and calloc() work for allocating memory, and of course free() for de-allocating memory.

But he did "i = 53", not "*i = 53".

---

### Post by dwhitney67 on 2009-09-21
> **Arndt said:**
> But he did "i = 53", not "*i = 53".

Oops, I misread the OPs code.

---

### Post by napsy on 2009-09-21
> **tom66 said:**
> The thing is, I've always been able to create int* pointers and work with them directly without assigning them an address, it seems like the runtime does this automatically...

```

#include <stdio.h>

int main()
{
	int *i;
	i = 53;
	printf("%d, %d\n", i, &i);
}

```

Output: 53, -1079642224

Am I going about this the wrong way??


In your sample code, you first declare a pointer to int. The storage for the pointer will be allocated automatically since the variable is declared 'auto' by the compiler. The life span of the i variable terminates when the function main() ends (which also ends the program in your case). The storage for i will be automatically deallocated. 

But the storage that is necessary to store an 'int' is not yet allocated since this is your job. The initial value of your i variable is undefined so it's also undefined what happens if you try to read or write from the location i points at (the value i stores).


To get a valid memory position that is large enough to store the int type (which is 4 bytes), you have to ask your operating system to get the valid address. This is what malloc() does. But malloc requires a size parameter. You can get a sice of a specific type with the sizeof operator. To put it all together, this is how you would get enogh memory to store an int from malloc().

i = malloc(sizeof(int))

now i will contain a valid memory address. To store data into the memory address, you use the dereference operator * (asterisk):

*i = 12;

which literally means: store the right value 12 to the location where i is pointing at (this *i). If you simply use the assignment operator like:

i = 12;

you will effectively overwrite the memory address that malloc() gave you with the value 12, which is probably not what you want.

---

### Post by phrostbyte on 2009-09-21
[http://www.youtube.com/watch?v=6pmWojisM_E](http://www.youtube.com/watch?v=6pmWojisM_E)

:P

---

### Post by tom66 on 2009-09-21
Thanks guys... I'll try to get it working.

---

### Post by ve4cib on 2009-09-21
> **phrostbyte said:**
> [http://www.youtube.com/watch?v=6pmWojisM_E](http://www.youtube.com/watch?v=6pmWojisM_E)

Pointer Fun with Binky is **awesome**.  We had to watch it in a couple of my comp sci classes back in university when we were first looking at pointers in C/++.  Simple, memorable explanation.  Five stars.

---

