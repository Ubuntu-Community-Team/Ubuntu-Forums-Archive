---
title: "[SOLVED] [C] Passing a string into a function warning"
date: 2008-12-21
forum: Programming Talk
---

### Post by OutOfReach on 2008-12-21
I have this code from an exercise I was doing from my book:
```

#include <stdio.h>
#include <string.h>
#include <stdbool.h>

/* A small exercise from Chapter 10 of Programming in C. */

// Prototypes
void insertString(char string[], int index, char insertString[]);

int main(void)
{
    char text[] = {"the wrong son"};
    char text2[] = {"per"};

    printf("%s\n", text);
    printf("%s\n", text2);

    insertString(text, 10, text2);

    printf("The new string is: %s\n", text);

    return 0;
}

void insertString(char string[], int index, char insertString[])
{
    int length = strlen(string);
    int inLength = strlen(insertString);
    int i, j;
    char tmpString[length];

    strcpy(tmpString, string);

    for (i=0, j=index; i < inLength; i++, j++)
    {
        string[j] = insertString[i];
    }

    for (i=index; j < (length+inLength); i++, j++)
    {
        string[j] = tmpString[i];
    }

    string[j] = '\0';   /* Finish it off with the string terminator */
}

```

Yes, the insertString() function might not be the best but it works and I'm still pretty new to all this.
Anyways, when I compile in Code::Blocks I get the following warnings:
```

warning: deprecated conversion from string constant to &#8216;char*&#8217;
warning: deprecated conversion from string constant to &#8216;char*&#8217;

```

On the line of: ```
insertString(text, 10, text2);
``` in the main() function.

When I compile by command line I get no warnings, odd. When I run the program, well, here's the output:
```

the wrong son
per
The new string is: the wrong person
Segmentation fault

```

Any help? I'm really stumped on this one.

---

### Post by dwhitney67 on 2008-12-21
Strange that you get compiler warnings; I did not.  I used gcc -Wall -pedantic -D_GNU_SOURCE -std=gnu99 to compile.

As for the application, it does generate a segmentation violation during runtime.  This is because you are attempting to stuff additional characters into a fixed-length character array (text).

---

### Post by Arylon on 2008-12-21
change ```
void insertString(char string[], int index, char insertString[])
``` to ```
void insertString(char* string, int index, char* insertString)
``` I think this will fix the compiler warnings. The segfault is because your original string was declared to be exactly the size of the text within it, leaving no room to add characters later.

---

### Post by monkeyking on 2008-12-21
no segfault for me.

try using gdb or valgrind.

---

### Post by monkeyking on 2008-12-21
what compiler version are you using.

---

### Post by fyplinux on 2008-12-21
There 's the problems:

0. basically, the argument char string[] cann't be modified.

1. j might be out of boundary, the maximum value of j is length-1

  for (i=0, j=index; i < inLength ; i++, j++)
    {
        string[j] = insertString[i];
    }


2. j will definetly out of boundary, as string 's length is less than length+inLength

    for (i=index; j < (length+inLength); i++, j++)
    {
        string[j] = tmpString[i];
    }


The possible solution:  allocate the memory for the new string, copy the source chars into the new string, then return the new string. Don't forget to free the memory if the new string if not needed any more

---

### Post by dwhitney67 on 2008-12-21
> **monkeyking said:**
> what compiler version are you using.

This is the version I am using:
```

$ gcc --version
gcc (GCC) 4.3.0 20080428 (Red Hat 4.3.0-8)

```

---

### Post by OutOfReach on 2008-12-21
Wow, fast replies.

> **Arylon said:**
> The segfault is because your original string was declared to be exactly the size of the text within it, leaving no room to add characters later.

Aha! That worked, how silly of me. Thank you, to all of you.

---

### Post by dwhitney67 on 2008-12-21
> **fyplinux said:**
> ...

The possible solution:  allocate the memory for the new string, copy the source chars into the new string, then return the new string. Don't forget to free the memory if the new string if not needed any more

+1.

The solution, as you noted above, is quite easy to implement.  It took me less than a minute.  Let's see if the OP can do it.

---

### Post by monkeyking on 2008-12-21
[PHP]
gcc --version
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[/PHP]

---

### Post by OutOfReach on 2008-12-21
> **fyplinux said:**
> 
The possible solution:  allocate the memory for the new string, copy the source chars into the new string, then return the new string. Don't forget to free the memory if the new string if not needed any more

I see what you're saying, infact that would be a better way of implementing my insertString() function, but right now I am not worried about, though I will indeed try it since I am always looking for ways to improve.

---

