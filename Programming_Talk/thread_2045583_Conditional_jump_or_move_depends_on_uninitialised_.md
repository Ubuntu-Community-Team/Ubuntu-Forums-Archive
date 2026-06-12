---
title: "Conditional jump or move depends on uninitialised value(s)"
date: 2012-08-21
forum: Programming Talk
---

### Post by Datweakfreak on 2012-08-21
Hi, I'm writing a simple program that returns regex patterns parsed from a string.

```
#include <stdio.h>
#include <string.h>
#include <pcre.h>

char **regexMatch(char *re, char *txt)
{
    const char *error;
    int erroffset;
    int ovector[186];
    int substrCount;

    pcre *r =  pcre_compile(re, PCRE_CASELESS|PCRE_DOTALL, &error, &erroffset, NULL);
    int rc = pcre_exec(r, NULL, txt, strlen(txt), 0, 0, ovector, 186);
    char **substr = malloc(rc * 1024 * sizeof(char));
    printf("%d\n", rc);

    if (rc > 0) {
        for (substrCount = 1; substrCount <= rc; substrCount++) {
            pcre_copy_substring(txt, ovector, rc, substrCount, substr[substrCount - 1], 1024);
        }
    }

    printf("%s", substr);

    return substr;
}

int main(void)
{
    char *str = "say \"string\"";
    char *pattern = "((?:[a-z][a-z0-9_]*))(\\s+)(\".*?\")";
    char **restr = regexMatch(pattern, str);

    printf("\n%s\n", restr);

    free(restr);

    return 0;
}
```Running this segfaults at the line containing pcre_copy_substring. Here's the valgrind output [**pastie**]("http://pastie.org/4563026"). I'm not sure where I'm messing up. When I replace:

```
char **substr = malloc(rc * 1024 * sizeof(char));
```with

```
char substr[rc][1024];
```The returned string is not the whole string (**say "string"**), but just **say**.

Thanks!

---

### Post by dwhitney67 on 2012-08-21
Without seeing the function prototype for pcre_copy_string(), I suspect that the problem is with your declaration here:
```

char **substr = malloc(rc * 1024 * sizeof(char));

```
Either a) you want to declare an array of chars, for which the declaration is incorrect, or b) you want to declare an array of strings, for which then the malloc() parameter is incorrect.

I'll guess it is 'a'; try modifying your code to this:
```

**char *substr** = malloc(rc * 1024 * sizeof(char));

```
If pcre_copy_string() requires a char**, then pass the address of substr.
```

pcre_copy_string(..., &substr, ...);

```

---

### Post by Datweakfreak on 2012-08-21
I wanted to declare an array of strings, so I used char **. 

And pcre_copy_substring() takes char * argument, so I thought I'd subscript substr with [substrCount - 1], so isn't that a char * if I'm not mistaken?

---

### Post by dwhitney67 on 2012-08-21
substrCount is uninitialized.  For all you know, it is set to MAX_INT.  So that is problem #1.

Problem #2: If you want to declare an array of strings, then the declaration should appear something like:
```

int N = 10;
char **substr = malloc(N * **sizeof(char*)**);

```
The code above declares an array of pointers to strings, but space for the strings themselves have not been declared.

It would be immensely helpful to know how substr gets populated.  Is it by that function pcre_copy_stringt()?

Please, give detailed information with your response.


P.S.  IMHO, you have nipped too much with this project; you should revisit your reference material to study pointers and arrays.  If you pass an array to a function, the function will have no idea what size that array is unless you specifically pass along size as a parameter.  Think along the lines of the main() function that accepts argc (int) and argv (which is an array of strings).

---

