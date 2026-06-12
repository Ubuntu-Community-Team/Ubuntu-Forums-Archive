---
title: "Append a C string with a single character"
date: 2008-12-19
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-19
How to add a char to the end of a string in C? strcat doesnt work :(

---

### Post by Bachstelze on 2008-12-19
Here's a way, there must be tons of others:

```
firas@nobue ~ % cat test.c
#include <stdio.h>
#include <string.h>

void append(char* s, char c)
{
        int len = strlen(s);
        s[len] = c;
        s[len+1] = '\0';
}

int main(void)
{
        char str[256] = "hello";
        char c = 'o';

        append(str, c);

        printf("%s\n", str);
        return 0;
}

firas@nobue ~ % cc -o test test.c
firas@nobue ~ % ./test
helloo

```

---

### Post by stchman on 2008-12-19
> **crazyfuturamanoob said:**
> How to add a char to the end of a string in C? strcat doesnt work :(

Of course strcat will work.

Remember C string functions actually use character arrays.

This statement will add or append a character on to the end of a character array.

Assume 

char str1[10] = "Hello";

strcat( "a", str1 );

The output will be Helloa.

Also if you want to just add a single character then you can do also do this.

char str1[10] = "Hello";

str1[ strlen(str1) ] = 'a';

The strlen function returns the length of a string.

---

### Post by ad_267 on 2008-12-19
You need to make sure the length of the array is long enough to take both the original string, the string you're appending and \0.

---

### Post by scourge on 2008-12-19
> **HymnToLife said:**
> Here's a way, there must be tons of others:

```
void append(char* s, char c)
{
        s[strlen(s)] = c;
        s[strlen(s)+1] = '\0';
}
```

That's not going to work. What will the second strlen() return if there's no terminating '\0' at the end?

This should work:
```

int len = strlen(s);
s[len] = c;
s[len + 1] = '\0';

```

---

### Post by Bachstelze on 2008-12-19
It did work here but yeah, that's assuming the string was initialized, which is not always the case... And anyway, there are two calls to [font="monospace"]strlen()[/font] which are redundant.

Fixed anyway.

---

### Post by stroyan on 2008-12-19
C strings don't have any standard way to determine the amount of allocated storage.
A general solution will require allocating storage for a new string.
And that will require that the storage for the new string is eventually freed.
You could use malloc to allocate the storage.
Or you could use the linux specific asprintf function
to allocate the storage and combine the old string and
character into a new string.
```

#define _GNU_SOURCE
#include <stdio.h>

char *append(const char *oldstring, const char c)
{
    int result;
    char *newstring;
    result = asprintf(&newstring, "%s%c", oldstring, c);
    if (result == -1) newstring = NULL;
    return newstring;
}

int main(int argc, char *argv[])
{
    char *s = "string";
    char *s2;
    char c = 'X';
    s2 = append(s, c);
    if (s2 == NULL) {
	printf("allocation failed\n");
	return 1;
    }
    printf("appending %c to %s gives %s\n", c, s, s2);
    free(s2);
    return 0;
}

```

---

### Post by crazyfuturamanoob on 2008-12-20
Compiler doesn't like unsigned string. How can I get it working with this?
```

unsigned char string[200];

```

Edit: unsigned char seems to work with signed string. Solved :)

---

