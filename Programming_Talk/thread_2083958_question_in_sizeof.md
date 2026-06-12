---
title: "question in sizeof"
date: 2012-11-14
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-14
Hey,
I have a question regarding the sizeof operator. But I think it translates to my understanding of pointers.

```

int arr[] = {1,2,3,4,5};

int main(void)
{
 printf("\nsizeof(arr) == %d",sizeof(arr));
 
 return 0;
}

```

Now I know that this programs outputs sizeof(int*) * 4 == 20 bytes.
But I have a problem here. [b]Since arr is of data type int*
. The name of an array holds the address of the first element of the array, right ? Here the first element is an integer, resulting in arr being of type int*.[/b] So shouldn't sizeof(arr) just return sizeof(int*) which is 4 bytes ?

Thanks.
Please advise.

---

### Post by spjackson on 2012-11-14
> **IAMTubby said:**
> Hey,
Now I know that this programs outputs sizeof(int*) * 4 == 20 bytes.

No. It is not an array of (int *); it is an array of (int). With 32-bit integers the result is 20.

sizeof(int) * 5 == 4 * 5 == 20

It is still 20 on 64-bit Ubuntu which has 32-bit integers but 64-bit pointers.

> 
But I have a problem here. [b]Since arr is of data type int*
. The name of an array holds the address of the first element of the array, right ? Here the first element is an integer, resulting in arr being of type int*.[/b] So shouldn't sizeof(arr) just return sizeof(int*) which is 4 bytes ?


Arrays and pointers in C are similar and the name of an array can be used as a pointer to the first element in **some** contexts. However, they are not the same thing. For example, you cannot do:
```

  arr++;

```

But you can do:
```

  int * p = arr;

  p++;

```

So when you say "arr is of data type int*", you are mistaken: the type of arr is "int[5]" or "array[5] of int".

Note that an array as a function parameter is a special case and is **equivalent** to a pointer to the first element, so you can increment it, and its size is the size of a pointer.

```

#include <stdio.h>

int arr[] = {1,2,3,4,5};

void foo(int a[])
{
 printf("sizeof(a) == %zd\n",sizeof(a));
}

int main(void)
{
 printf("\nsizeof(arr) == %zd\n",sizeof(arr));

 foo(arr);
 
 return 0;
}

```

---

### Post by IAMTubby on 2012-11-14
> **spjackson said:**
> 
spjackson, thanks for the reply.

> 
So when you say "arr is of data type int*", you are mistaken: the type of arr is "int[5]" or "array[5] of int".

Sir, I understand I'm wrong here. But I'm still having a few problems convincing myself because,
```

int arr[] = {1,2,3};
int* ptr;
ptr = arr; //This is valid

```
So since only 2 **similar/same** data types can be assigned to each other, I find it hard convince myself that arr is not of type int*.Isn't my question valid? Isn't this slightly confusing in C ? 
Or should I convince myself that this is just a special case ?

> 
Note that an array as a function parameter is a special case and is **equivalent** to a pointer to the first element, so you can increment it, and its size is the size of a pointer.

Thanks for that :)

---

### Post by spjackson on 2012-11-14
> **IAMTubby said:**
> 
```

int arr[] = {1,2,3};
int* ptr;
ptr = arr; //This is valid

```
So since only 2 **similar/same** data types can be assigned to each other, I find it hard convince myself that arr is not of type int*.

They cannot be assigned to **each other**. An array can be assigned to a pointer, but a pointer cannot be assigned to an array.

Here is the relevant wording from the C99 standard.
> 
Except when it is the operand of the **sizeof** operator or the unary **&** operator, or is a string literal used to initialize an array, an expression that has type "array of type" is converted to an expression with type "pointer to type" that points to the initial element of the array object and is not an lvalue.


Because this conversion takes place automatically in many contexts, you are interpreting it as though an array **is** a pointer. It is not. It is **converted** to a pointer, with the exceptions described above. You can assign a double to an int, and an int to a double. This does not mean that an int is a double. Conversions take place when you do this.

---

### Post by IAMTubby on 2012-11-14
> **spjackson said:**
> They cannot be assigned to **each other**. An array can be assigned to a pointer, but a pointer cannot be assigned to an array.

Here is the relevant wording from the C99 standard.


Because this conversion takes place automatically in many contexts, you are interpreting it as though an array **is** a pointer. It is not. It is **converted** to a pointer, with the exceptions described above. You can assign a double to an int, and an int to a double. This does not mean that an int is a double. Conversions take place when you do this.
spjackson, Thank you so much. The explanation was very clear. :)
Marking the thread as solved.

1) What does c99 standard mean by > or is a string literal used to initialize an array
Is it like
```

char** strp;
char s[] = "hello";
char s1[]= "world";
strp = {s,s+1}

```
2)Where can I download the c99 standard. I tried here
[http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf)
but it doesn't have the wordings above.

---

### Post by spjackson on 2012-11-14
> **IAMTubby said:**
> 
1) What does c99 standard mean by "or is a string literal used to initialize an array"
Is it like
```


char s[] = "hello";
char s1[]= "world";


```
Yes.
[QUOTE]
2)Where can I download the c99 standard. I tried here
[http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf)
but it doesn't have the wordings above.
It is in that link, page 46, section 6.3.2.1, paragraph 3.

---

### Post by IAMTubby on 2012-11-14
> **spjackson said:**
> [QUOTE=IAMTubby;12353904]
1) What does c99 standard mean by "or is a string literal used to initialize an array"
Is it like
```


char s[] = "hello";
char s1[]= "world";


```
Yes.

It is in that link, page 46, section 6.3.2.1, paragraph 3.
Thanks a lot Sir.

---

### Post by Bachstelze on 2012-11-14
> **IAMTubby said:**
> 
```

char** strp;
char s[] = "hello";
char s1[]= "world";
strp = {s,s+1}

```

I have no idea what you meant to say with this code, but it is not legal C.

---

### Post by IAMTubby on 2012-11-15
> **Bachstelze said:**
> I have no idea what you meant to say with this code, but it is not legal C.
Bachstelze, I'm very sorry. I have no idea what I've written either. Here is the corrected code however.

```

#include <stdio.h>
#include <malloc.h>

int main(void)
{
 char** strp;
 char s[] = "Thanks ";
 char s1[]= "Bachstelze !";

 strp = malloc(200 * sizeof(char));
 *strp = malloc(200 * sizeof(char));

 *strp = s;
 *(strp + 1) = s1;

 printf("\nThe first string is : [%s]",*strp);
 printf("\nThe second string is : [%s]",*(strp + 1));

 return 0;
}

```

However, you just made me open a can of worms, there are so many doubts in my mind right now. But I would like to think over it once again before posting. Thanks a lot once again :)

---

### Post by Bachstelze on 2012-11-15
That's still very weird. I think what you meant is:

```
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 char** strp;
 char s[] = "Thanks ";
 char s1[]= "Bachstelze !";

 strp = malloc(2*sizeof(char*));

 strp[0] = s;
 strp[1] = s1;

 printf("\nThe first string is : [%s]", strp[0]);
 printf("\nThe second string is : [%s]", strp[1]);

 free(strp);
 return 0;
}
```

I changed your * notation to array notation because it is cleaner, but it's the same thing internally of course... The real problem is that your malloc()s were wrong. Also, malloc() is in stdlib.h. malloc.h is non-standard.

EDIT: Also, there's no real point in allocating memory for strp dynamically...

---

