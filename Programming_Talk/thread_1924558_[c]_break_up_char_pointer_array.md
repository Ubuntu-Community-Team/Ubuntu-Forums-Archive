---
title: "[c] break up char pointer array"
date: 2012-02-12
forum: Programming Talk
---

### Post by Xender1 on 2012-02-12
I have a function which returns a pointer to a string of chars (max being max size in bytes)

```

int read_ret(char *message, int max);
read_ret(&msg, 80);

```

I know this msg has two strings (first name/last name each max 40 bytes), my question is how do I extract this out? I have allocated 2 other char arrays to be of size 40 

```

char *firstname; char *lastname;
firstname = (char *) malloc(40);
lastname = (char *) malloc(40);

```

Should I use strncopy to but the msg into firstname/lastname, but then how do i go about using a range for lastname. Or is it as simple as assigning firstname = msg[0] and lastname=msg[41] or something like that? 

Essentially I know where msg is in memory, just how do I assign firstname to equal the memory and lastname to equal the memory at the correct spot.

Thank you very much.

---

### Post by trent.josephsen on 2012-02-13
It looks like you have a function that returns an int.  Assuming you meant to say "I have a function that populates an array of chars given to it".

When you figure out why this code works and is well-defined (unless I have made a monumental error), you'll be well equipped to answer your own question:
```
char *s = "hello, world";
puts(s + 7);
```

If max is a size, it would probably be more prudent to declare it as a size_t rather than just an int.

Finally, **don't cast the result of malloc()**!

---

### Post by gateway67 on 2012-02-13
> **Xender1 said:**
> 
I know this msg has two strings (first name/last name each max 40 bytes), my question is how do I extract this out? I have allocated 2 other char arrays to be of size 40 

You indicated above what the max size (length) of a first name or last name may be, however you did not specify what would be the minimum size (presumably a single character would suffice?).  Anyhow, you shouldn't assume the last name begins at offset 41 unless the conjoined string is set up that way.

Is there any field separator between the first and last names?  If so, then it may be possible to use strchr() to find that point in the string, thus giving you a reference point as to where one string ends and the next begins.

Maybe the following will give an idea:
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    const char* first_last = "Fred Flintstone";

    const char* space = strchr(first_last, ' ');    // assume space-character separator
    const char* end   = strchr(first_last, '\0');   // look for terminating null-character

#ifndef _GNU_SOURCE

    char* first = malloc(space - first_last + 1);
    char* last  = malloc(end - space);

    snprintf(first, space - first_last + 1, "%s", first_last);
    snprintf(last,  end - space + 1, "%s", space + 1);

#else

    char* first = strndup(first_last, space - first_last);
    char* last  = strndup(space + 1, end - space);

#endif

    printf("first name is: %s\n", first);
    printf("last name is : %s\n", last);

    free(first);
    free(last);

    return 0;
}

```

---

