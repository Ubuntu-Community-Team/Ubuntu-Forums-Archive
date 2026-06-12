---
title: "C Data Types"
date: 2007-09-24
forum: Programming Talk
---

### Post by WastingBody on 2007-09-24
Is there a byte data type for C? I used to use Visual Studio, and it had the byte data type. I need to use it for a project that I am working on, but the byte data type doesn't seem to exist. Help is much appreciated.

---

### Post by hod139 on 2007-09-24
[http://www.cppreference.com/data_types.html](http://www.cppreference.com/data_types.html) 

There is no byte datatype.  The size of the data types is also architecture dependent.  You can use the command sizeof to determine the size (in bytes) of a type.  Usually, a char is one byte.

**Edit:** I should add, if you really need to guarantee that something is a byte, you have to use the C99 standard header stdint.h, which defines (among others) the type
uint8_t
which will be 8 bits.  But, this will require a compiler that implements the C99 standard.

---

### Post by WastingBody on 2007-09-24
I'll just use char. It seems like the easiest thing to do.

---

### Post by Compyx on 2007-09-25
You'll want to use unsigned char, since plain char can be either signed or unsigned, depending on the implementation.

For convenience, you could do something like:
```

typedef unsigned char byte;

```

And about the 'size' command, there is no such thing. I think hod139 was thinking of the **sizeof** operator, which tells you the size of an object or type in C-bytes (which aren't always an octet). sizeof(char) is guaranteed to be 1 by the C standard.

To check the size of a char type in bits, use something like the following:
```

#include <stdio.h>
#include <stdlib.h>
#include <limits.h>

int main(void)
{
    printf("Number of bits in a 'char' = %d\n", CHAR_BIT);
    return EXIT_SUCCESS;
}

```

CHAR_BIT is guaranteed to be at least 8, but can be more.

If you know your code will break if CHAR_BIT is more than 8, you can do something like:
```

#include <limits.h>
#if CHAR_BIT > 8
  #error "Sorry, I only work correctly when a char is 8 bits!"
#endif

```


HTH

---

### Post by hod139 on 2007-09-25
> **Compyx said:**
> YAnd about the 'size' command, there is no such thing. I think hod139 was thinking of the **sizeof** operator, which tells you the size of an object or type in C-bytes (which aren't always an octet). sizeof(char) is guaranteed to be 1 by the C standard.
Oops!!  Thanks for catching that.  I fixed it in my previous post.

---

