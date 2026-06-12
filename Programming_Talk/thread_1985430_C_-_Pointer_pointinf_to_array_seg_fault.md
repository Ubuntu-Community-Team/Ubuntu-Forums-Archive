---
title: "C - Pointer pointinf to array seg fault"
date: 2012-05-23
forum: Programming Talk
---

### Post by stamatiou on 2012-05-23
I have written this C program:
```
#include <stdio.h>
#include <string.h>

int main(void)  {
                char *array = "abc", *pointer;
                printf("sizeof(array) = %d\tsizeof array = %d\n",sizeof(array),sizeof array);
                printf("sizeof(pointer) = %d\t sizeof pointer = %d\n",sizeof(pointer), sizeof pointer);
                strcpy(array, "abcd");
                pointer = array;
                putchar('\n');
                printf("sizeof(array) = %d\tsizeof array = %d\n",sizeof(array),sizeof array);
                printf("sizeof(pointer) = %d\t sizeof pointer = %d\n",sizeof(pointer), sizeof pointer);
                return 0;
}

```
But when I execute it I get this output:
```
sizeof(array) = 4       sizeof array = 4
sizeof(pointer) = 4      sizeof pointer = 4
Segmentation fault

```
Why do I get that segmentation fault?

Thanks in advance.

---

### Post by PaulM1985 on 2012-05-23
You define array to point to a string which is 3 characters long, "abc".  When you do strcpy(array, "abcd"), you are saying, put 4 characters into the "array".  Since you initially allocated array to be 3 characters long, the 4 characters you are copying accross don't fit, so you get a segmentation fault.

Paul

EDIT: At least I think this is the issue, I haven't checked it through.  Put more print statements in so you can narrow down to the exact line that is producing the seg fault.

---

### Post by pbrane on 2012-05-23
Your array has been initialized to "abc" plus a null byte. Sizeof(array) == 4, then you tried to copy "abcd" plus a null byte (5 elements) to your 4 element array.

This would work...
```

char array[5], *pointer;

```

Or use malloc, realloc functions.

---

### Post by stamatiou on 2012-05-23
Million thanks! Stupid mistake of mine :P

---

### Post by stamatiou on 2012-05-23
> **pbrane said:**
> Your array has been initialized to "abc" plus a null byte. Sizeof(array) == 4, then you tried to copy "abcd" plus a null byte (5 elements) to your 4 element array.

This would work...
```

char array[5], *pointer;

```

Or use malloc, realloc functions.
And why is this illegal:
```
#include <stdio.h>
#include <string.h>

int main(void)  {
                char *array = "abcde", *pointer;
                printf("sizeof(array) = %d\tsizeof array = %d\n",sizeof(array),sizeof array);
                printf("sizeof(pointer) = %d\t sizeof pointer = %d\n",sizeof(pointer), sizeof pointer);
                strcpy(array, "abcd");
                pointer = array;
                putchar('\n');
                printf("sizeof(array) = %d\tsizeof array = %d\n",sizeof(array),sizeof array);
                printf("sizeof(pointer) = %d\t sizeof pointer = %d\n",sizeof(pointer), sizeof pointer);
                return 0;
}

```

---

### Post by GeneralZod on 2012-05-23
```

char *array = "abcde", *pointer;
...
                strcpy(array, "abcd");

```

You are attempting to copy over the string-literal "abcde", which is undefined behaviour.   Behind the scenes: you are attempting to overwrite read-only memory.

---

### Post by stamatiou on 2012-05-23
> **GeneralZod said:**
> ```

char *array = "abcde", *pointer;
...
                strcpy(array, "abcd");

```

You are attempting to copy over the string-literal "abcde", which is undefined behaviour.   Behind the scenes: you are attempting to overwrite read-only memory.
:lolflag:I was about to tell that one :P The problem would be solved if the string literal was an array :D

---

