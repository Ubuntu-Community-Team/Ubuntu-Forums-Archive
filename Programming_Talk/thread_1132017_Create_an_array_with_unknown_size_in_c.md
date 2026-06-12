---
title: "Create an array with unknown size in c?"
date: 2009-04-21
forum: Programming Talk
---

### Post by nite owl on 2009-04-21
I am looking to create an array of chars with an unknown size and I know you use the 'malloc' function, but I am unsure of the exact way to do it. I have looked at tutorials on google, but they seem to be confusing and never give a straight forward basic explanation.

So basically how do you create a char array with an unknown size at compile time?

---

### Post by Arndt on 2009-04-21
> **nite owl said:**
> I am looking to create an array of chars with an unknown size and I know you use the 'malloc' function, but I am unsure of the exact way to do it. I have looked at tutorials on google, but they seem to be confusing and never give a straight forward basic explanation.

So basically how do you create a char array with an unknown size at compile time?

```
char *p = malloc(size);
```

This is so simple that I think I must have missed what you are perceiving as the problem. Explain further in that case.

---

### Post by terrax on 2009-04-21
Lets say you have to store "hello" into an unknown size char array.

Then just.
```

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
char *array;

   array = malloc(sizeof("hello")); //<- Make your char pointer, point at the newly created space in memory.
   strcpy(array,"hello");           //<- Copy "hello" into the newly created array of chars.
   printf("%s",array);

   return 0;
}

```


If you want to have space for 10 chars in your array, then just use sizeof(10*char).
Then malloc will allocate 10*8 bytes in you memory, and point your array pointer at it.

---

### Post by Simian Man on 2009-04-21
C99 also has support for variable length arrays on the stack as the following demonstrates:
```

#include <stdio.h>

int main( )
{
  int size;
  printf("How large? ");
  scanf("%d", &size);

  int array[size];

  printf("Size=%d\n", sizeof(array)/sizeof(int));

}

```

This is a very nice feature, but keep in mind that many C compilers, besides gcc, don't support C99.

---

### Post by Arndt on 2009-04-21
> **Simian Man said:**
> C99 also has support for variable length arrays on the stack as the following demonstrates:
```

#include <stdio.h>

int main( )
{
  int size;
  printf("How large? ");
  scanf("%d", &size);

  int array[size];

  printf("Size=%d\n", sizeof(array)/sizeof(int));

}

```

This is a very nice feature, but keep in mind that many C compilers, besides gcc, don't support C99.

Also, note that the stack is usually much more limited; it's not certain you can allocate very large arrays there.

---

### Post by Arndt on 2009-04-21
> **terrax said:**
> Lets say you have to store "hello" into an unknown size char array.

Then just.
```

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
char *array;

   array = malloc(sizeof("hello")); //<- Make your char pointer, point at the newly created space in memory.
   strcpy(array,"hello");           //<- Copy "hello" into the newly created array of chars.
   printf("%s",array);

   return 0;
}

```


If you want to have space for 10 chars in your array, then just use sizeof(10*char).
Then malloc will allocate 10*8 bytes in you memory, and point your array pointer at it.

sizeof(10*char) won't work. It's 10*sizeof(char). sizeof(char) is defined to be 1, but it's often written out all the same, for clarity.

10*8 bits will be allocated, by the way, not bytes.

---

### Post by Tony Flury on 2009-04-21
> **terrax said:**
> Lets say you have to store "hello" into an unknown size char array.

Then just.
```

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
char *array;

   array = malloc(sizeof("hello")); //<- Make your char pointer, point at the newly created space in memory.
   strcpy(array,"hello");           //<- Copy "hello" into the newly created array of chars.
   printf("%s",array);

   return 0;
}

```


```

array = malloc(sizeof("hello"));

```
wont work - as the sizeof as a string is the just the size of a pointer - i think you meant to use strlen.

that full program might work - but only because it is trivial. If you used that code segment in a bigger program you would discover that you may well have overflowed (and cause other problems) since the array you allocated (since on most machines the sizeof a pointer is 4 bytes, and the string "hello" is 6 bytes - including the '/0').

---

### Post by Arndt on 2009-04-22
> **Tony Flury said:**
> ```

array = malloc(sizeof("hello"));

```
wont work - as the sizeof as a string is the just the size of a pointer - i think you meant to use strlen.



No, sizeof actually works, because it gets an actual string constant, which is not converted to a pointer at that point, as it is in most other places (note that **char s[]="hello";** also doesn't convert to a pointer).

Using strlen is fine, but beware that it doesn't count the final Nul character, so it has to be strlen(str)+1.

---

### Post by samsung_11112 on 2011-10-17
I believe this will work?

#include <iostream>
#include <cstring>
using namespace std;

int main()
{
    char *x;
    char *p;
    cin>>p;

    x=new char[strlen(p)+1];

    strcpy(x,p);
    cout <<x;


    return 0;
}

---

### Post by lisati on 2011-10-17
Back to sleep....

---

