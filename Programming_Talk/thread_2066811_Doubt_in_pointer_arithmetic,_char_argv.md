---
title: "Doubt in pointer arithmetic, char** argv"
date: 2012-10-05
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-05
Hey,
Just like you declare an array of string using 
```

char* argv[] = {"one","two","three"};

```
Is it possible to **declare** the same using char** argv ?
I know how to receive an array of strings as a parameter using
```

int main(int argc, char** argv)

```
and how to access the elements. But just wanted to know how to declare/define an array of strings.

Thanks.

---

### Post by dwhitney67 on 2012-10-05
First of all, for this particular declaration:
```

char* argv[] = {"one","two","three"};

```
you should get into the habit to declare it so that it is obvious to code readers that the string values cannot be modified.  Do something like this:
```

**const **char* argv[] = {"one","two","three"};

```

As for your second question, you can make an array of strings using something like this (which I have not compiled):
```

void some_function(int argc, char** argv);

...

// Allocate array that is capable of storing 3 strings and a NULL pointer.
int    myArgc = 3;
char** myArgv = malloc((myArgc + 1) * sizeof(char*));

myArgv[0] = strdup("One");
myArgv[1] = strdup("Two");
myArgv[2] = strdup("Three");
myArgv[4] = NULL;

some_function(myArgc, myArgv);

...

```

---

### Post by ofnuts on 2012-10-05
> **IAMTubby said:**
> Hey,
Just like you declare an array of string using 
```

char* argv[] = {"one","two","three"};

```Is it possible to **declare** the same using char** argv ?
I know how to receive an array of strings as a parameter using
```

int main(int argc, char** argv)

```and how to access the elements. But just wanted to know how to declare/define an array of strings.

Thanks.
No, you cannot initialize your array using "char **x" but once it is initialized you can refer to it that way, i.e.:
```

char *y[]={"1","2","3"};
char **x=y;

printf("%s\n",*x);
printf("%s\n",*(x+1));

```

---

### Post by IAMTubby on 2012-10-08
> **dwhitney67 said:**
> 
> **ofnuts said:**
> 
Ofnuts, dwhitney,
Thanks to both of you I have understood the concept very well. 
Basically, you can summarize this by saying that the cause of all this, is because, "The name of an array holds the address of the first element of the array", right ?

> 
you should get into the habit to declare it so that it is obvious to code readers that the string values cannot be modified.  Do something like this:
```

**const **char* argv[] = {"one","two","three"};

```

I get it, because if you keep changing the contents, the compiler will not know how much memory to allocate horizontally right?(The usage of the word "horizontally" was just to convey the point ; I just typed it and found it very cool :), so stuck with it)
I in fact, tried doing 
```

#include<stdio.h>

int main(void)
{
 char* argv[] = {"one","two","three"};

 printf("%s",*(argv + 1));

 printf("\nChanging contents ");
 strcpy(argv[1],"four");
 printf("%s",*(argv + 1));
 
 return 0;
}

```
and got a Segmentation Fault :)

> **ofnuts said:**
> 
```

char *y[]={"1","2","3"};
char **x=y;

printf("%s\n",*x);
printf("%s\n",*(x+1));

```
Okay, and just to test my understanding, to access individual characters, you would do this right ?
(This is to access the 2nd character of the second string)
```

printf("%c",*(*(argv  + 1) + 1);

```

---

### Post by IAMTubby on 2012-10-08
By the way, don't you think this should be allowed ? The compiler doesn't have to allocate any more memory. Just altering contents. 
```

#include<stdio.h>

int main(void)
{
 char* argv[] = {"one","two","three"};

 printf("%s",*(argv + 1));

 printf("\nChanging contents ");
 strcpy(argv[1],"123"); //**same memory requirement as the original contents ("one")**
 printf("%s",*(argv + 1));
 
 return 0;
}

```
PS : This was on a light note, I understand that uniformity has to be maintained :)

---

### Post by Bachstelze on 2012-10-08
> **IAMTubby said:**
> Ofnuts, dwhitney,
Thanks to both of you I have understood the concept very well. 
Basically, you can summarize this by saying that the cause of all this, is because, "The name of an array holds the address of the first element of the array", right ?

That's an adequate way to look at it, yes.

> I get it, because if you keep changing the contents, the compiler will not know how much memory to allocate horizontally right?(The usage of the word "horizontally" was just to convey the point ; I just typed it and found it very cool :), so stuck with it)
I in fact, tried doing 
```

#include<stdio.h>

int main(void)
{
 char* argv[] = {"one","two","three"};

 printf("%s",*(argv + 1));

 printf("\nChanging contents ");
 strcpy(argv[1],"four");
 printf("%s",*(argv + 1));
 
 return 0;
}

```
and got a Segmentation Fault :)

1. You forgot to include string.h.
2. *(argv + 1) is ugly. Do argv[1], which means the same thing.
3. The problem here is not how much memory is allocated but where it is allocated. In general, when you have a string literal, memory for it is allocated in a read-only area of memory, and so you can't write to it. You can, however, do something like this:

```
#include <stdio.h>
#include <string.h>

int main(void)
{
 char* argv[] = {"one","two","three"};

 printf("%s", argv[1]);

 printf("\nChanging contents ");
 char string[] = "supercalifragilisticexpialidocious";
 argv[1] = string;
 printf("%s\n", argv[1]);
 
 return 0;
}

```

> Okay, and just to test my understanding, to access individual characters, you would do this right ?
(This is to access the 2nd character of the second string)
```

printf("%c",*(*(argv  + 1) + 1);

```

This is correct but even uglier. Do argv[1][1].

---

### Post by Bachstelze on 2012-10-08
Also, why name your array argv?

---

### Post by IAMTubby on 2012-10-08
> **Bachstelze said:**
> 
```
#include <stdio.h>
#include <string.h>

int main(void)
{
 char* argv[] = {"one","two","three"};

 printf("%s", argv[1]);

 printf("\nChanging contents ");
 char string[] = "supercalifragilisticexpialidocious";
 argv[1] = string;
 printf("%s\n", argv[1]);
 
 return 0;
}

```

Thanks Bachstelze for the replies. 

> 
The problem here is not how much memory is allocated but where it is allocated. In general, when you have a string literal, memory for it is allocated in a read-only area of memory, and so you can't write to it.

Sorry for being repetative about this question. But, how much memory is allocated, is also important right ? So, on declaring such a huge string/overwriting, do all the other array elements get arranged accordingly ? Or it really doesn't matter because we are anyways holding only the starting address?

> 
Also, why name your array argv?

:) . I was trying to understand the concept of char** argv, and that's how I ended up exploring this. So stuck with the name unknowingly.

---

### Post by Bachstelze on 2012-10-08
argv is an array of pointers to char. All pointers always takes the same amount of space, regardless of the length of the string they point to. In my code above I replace a pointer with another pointer, the length of the string is irrelevant.

Before :

```

+---------+---------+---------+       +--------+
| argv[0] | argv[1] | argv[2] |       | string |
+---------+---------+---------+       +--------+
    |         |          |                |   
    |         |          |                |   
    v         v          v                v   
  +---+     +---+      +---+            +---+
  | o |     | t |      | t |            | s | 
  +---+     +---+      +---+            +---+ 
  | n |     | w |      | h |            | u | 
  +---+     +---+      +---+            +---+
  | e |     | o |      | r |            |...|
  +---+     +---+      +---+            +---+
  |\0 |     |\0 |      | e |            | u | 
  +---+     +---+      +---+            +---+
                       | e |            | s | 
                       +---+            +---+ 
                       |\0 |            |\0 |
                       +---+            +---+

```

After:

```
+---------+---------+---------+       +--------+
| argv[0] | argv[1] | argv[2] |       | string |
+---------+---------+---------+       +--------+
    |         |          |                |   
    |         +----------|----------------+
    v                    v                v
  +---+                +---+            +---+
  | o |                | t |            | s |
  +---+                +---+            +---+ 
  | n |                | h |            | u |
  +---+                +---+            +---+
  | e |                | r |            |...|
  +---+                +---+            +---+
  |\0 |                | e |            | u |
  +---+                +---+            +---+
                       | e |            | s |
                       +---+            +---+
                       |\0 |            |\0 |
                       +---+            +---+

```

The structure of the argv array has not changed, it still contains three elements of sizeof(char*) bytes each.

---

### Post by Bachstelze on 2012-10-08
In your code, you were trying to write to the memory area pointed by argv[1], that failed because it is read-only. In my code, I make argv[1] point somewhere else, it's totally different.

---

### Post by IAMTubby on 2012-10-09
> **Bachstelze said:**
> Thanks a lot Bachstelze for the wonderful reply.

> 
In my code above I replace a pointer with another pointer, the length of the string is irrelevant.

This part is now clear, thanks to your visual explanation.

But Sir, I still have a few problems understanding the difference between 
```

char* argv[] = {"one","two","three"};
strcpy(argv[1],"four");

```

and 

```

char* argv[] = {"one","two","three"};
char string[] = "supercalifragilisticexpialidocious";
argv[1] = string;

```

> 
In general, when you have a string literal, memory for it is allocated in a read-only area of memory, and so you can't write to it.

Sir, can you explain this line once again, with respect to the 2 code pieces above. A string literal ? 
I'm not able to understand the difference between  **strcpy(argv[1],"four");** and [b]char string[] = "supercalifragilisticexpialidocious";
argv[1] = string;[/b]

Thanks.

---

### Post by Bachstelze on 2012-10-09
> **Bachstelze said:**
> In your code, you were trying to write to the memory area pointed by argv[1], that failed because it is read-only. In my code, I make argv[1] point somewhere else, it's totally different.

^

---

### Post by IAMTubby on 2012-10-09
> **Bachstelze said:**
> 
Sir, I'm very sorry to have not read the second reply.
I understand now, especially after googling for the meaning of **"string literal"**.
A string literal in C is a sequence of characters enclosed within a quotation marks, and as you said, these are generally allocated in a read-only area of the memory.

Thanks a lot for clearing this :)

---

### Post by IAMTubby on 2012-10-11
> **Bachstelze said:**
> ^
Bachstelze, thanks a lot for your reply.
I had completely forgotten about all this, and was working on something else when I was faced with the same issue. Kept getting segmentation faults. 
Then I suddenly remembered about this issue and now it all works :)

Thanks a lot.

---

### Post by Bachstelze on 2012-10-11
> **IAMTubby said:**
> Bachstelze, thanks a lot for your reply.
I had completely forgotten about all this, and was working on something else when I was faced with the same issue. Kept getting segmentation faults. 
Then I suddenly remembered about this issue and now it all works :)

Thanks a lot.

Just because you don't get any segfaults doesn't mean you do everything right. At the very least, run it in valgrind, it will detect the most obvious mistakes (i.e., those that are triggered on every run).

---

### Post by StephenF on 2012-10-12
Overwriting string literals is not permitted by the language.
```

char *sl1 = "foo";
char *sl2 = "foo";
strcpy(sl1, "bar"); // wrong
sl1 = "bar"; // right

```
String literals on some architectures e.g. microcontrollers might well be stored in read only memory which would make modification absolutely impossible. Even if you could write to it sl2 might be pointing to the exact same memory location. The GNU C compiler merges duplicate string literals by default.

---

