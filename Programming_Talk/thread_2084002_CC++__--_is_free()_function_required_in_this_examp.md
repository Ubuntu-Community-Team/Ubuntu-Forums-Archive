---
title: "C/C++  -- is free() function required in this example?"
date: 2012-11-14
forum: Programming Talk
---

### Post by uncleheinz on 2012-11-14
Hello,

Here is a simple code snippet:

```


#include <stdio.h>
#include <stdlib.h>


/**
 * Converts character into string
 */
const char *char2str(char ch)
    {
    char *str = (char *)malloc(sizeof(char) * 2);

    if(str != NULL)
        {
        str[0] = ch;
        str[1] = '\0';
        }

    return (const char *)str;
    }


int main()
    {
    char letter = 'A';
    const char *word = char2str(letter);

    printf("%c\n%s\n", letter, word);

    return 0;
    }


```

I just don't understand, where exactly should I have to call this free() function. I can't do it inside char2str() function. So it made me wonder if free() function is actually required inside this particular code? Will it cause any memory leak if malloc() is called inside a non-void function and free() never used?

That char2str() probably has no practical usage in real life, but this is currently not the point.

---

### Post by ksprasad on 2012-11-14
Hi,
 
The above code does have memory leak as the allocated memory is not free'd anywhere. 
Usually we de-allocate the memory when it is no longer required. In the above example, you can add free statement before returning from main.
 
```

if(word  != NULL)
{
    free(word);
}

```
 
Regards,
ksprasad

---

### Post by uncleheinz on 2012-11-14
I also assumed that putting free(word); statement inside main() function solves all. But both of my compilers (GCC and G++) are somewhat unhappy.

GCC gives me warnings and notes but eventually it compiles.
G++ just gives me nasty errors.

---

### Post by ksprasad on 2012-11-14
Hi,
 
free function takes void * as parameter. But here we are passing const char *. So, you can typecast the passed parameter to to char * or void *
 
free((void *)word);
 
Regards,
ksprasad

---

### Post by uncleheinz on 2012-11-14
That solution works just perfectly. Thank you so much.

---

### Post by Bachstelze on 2012-11-14
Why do you make your function return const? I see no reason for it, and it forces you to typecast if you want to suppress warnings, which is generaly not a good thing to do if you can avoid it. The code below is better but you still have some real problems. What if char2str() returns NULL?

```
#include <stdio.h>
#include <stdlib.h>


/**
 * Converts character into string
 */
char *char2str(char ch)
{
    char *str = malloc(sizeof(char) * 2);

    if (str != NULL) {
        str[0] = ch;
        str[1] = '\0';
    }

    return str;
}


int main()
{
    char letter = 'A';
    char *word = char2str(letter);

    printf("%c\n%s\n", letter, word);

    free(word);
    return 0;
}

```

---

### Post by dwhitney67 on 2012-11-14
> **uncleheinz said:**
> 
GCC gives me warnings and notes but eventually it compiles.
G++ just gives me nasty errors.

Pick a language!  C and C++ are not the same, and are considered different programming languages.

It appears that you are programming in C, because stdio, malloc(), and free() are strong hints of so... thus stick to compiling with gcc.

If you opt to program in C++, use iostream, new, and delete... and compile with g++.

---

### Post by trent.josephsen on 2012-11-14
Second what dwhitney said.

If you do want to make it return "const char *", I'd consider making str static and returning a pointer to it, which eliminates the possibility of a memory leak as well as simplifying the code.

```
const char *char2str(char ch)
{
    static char str[2] = {0};
    str[0] = ch;
    return str;
}
```

This works because str has *static storage duration*, which means its contents don't become indeterminate when char2str returns and the name goes out of scope. Since there's only one copy of it, though, you will lose information if you call char2str multiple times in a row:

```
const char *s1, *s2;
s1 = char2str('a');
s2 = char2str('b');

puts(s1);
puts(s2);
```
This will print "b" twice because the second call to char2str overwrites the "a" that was already in str. For a short and simple program like yours this doesn't make a difference.

Another, idiomatic alternative is passing char2str a pointer to the string it is to modify. In this case I'd definitely leave off the const:

```
char *char2str(char *str, char ch)
{
    str[0] = ch;
    str[1] = 0;
    return str;
}
```

I'd prefer one of these over your solution or Bachstelze's because I'm allergic to dynamic memory, and I especially try to ensure that a *alloc() and its corresponding free() are always found in the same function (preferably within a few lines of each other). When I have to return a pointer to dynamically allocated memory, I name the function something ending in 'alloc' to remind me to free() the pointer it returns.

---

### Post by cgroza on 2012-11-16
I see that your program returns immediately after you use your value.
The operating system will free the memory after it returns. But if you use this code in a loop, not freeing will cause a memory leak.

---

