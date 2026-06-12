---
title: "C strings pointer manipulation problem"
date: 2011-07-01
forum: Programming Talk
---

### Post by cdiem on 2011-07-01
I have been trying to resolve the No1 of the Ruby quiz problems - [http://www.rubyquiz.com/quiz1.html](http://www.rubyquiz.com/quiz1.html) in C, but the program keeps complaining to me when I try to free my pointer. Please, can you help me find my error? Here's my code so far:

```

#include <string.h>
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

#define GROUP_LENGTH 5 // the words are in groups of 5 characters

char *to_alpha(char *msg);

int main(void)
{
    char msg[] = "Bla bla";
    printf("%s\n", to_alpha(msg));
    return EXIT_SUCCESS;
}

int exit_error(char * error)
{
    perror(error);
    return EXIT_FAILURE;
}

/*
 * Uppercases the message, removes non-alpha chars.
 * Adds X to the end of the message.
 */
char *to_alpha(char *msg)
{
    int len_duplicate; 
    char *duplicate;
    if ((duplicate = malloc(strlen(msg) + 1)) == NULL)
        exit_error("Null duplicate string");

    // pass throught the strings once, copy and uppercase
    // all letters [a-zA-Z]
    for (len_duplicate = 0; *msg; *msg++)
        if (isalpha(*msg))
        {   
            *duplicate++ = toupper(*msg);
            len_duplicate++;
        }   

    // append 'X' letters to the rest of the string
    // until it divides GROUP_LENGTH in a clean manner:
    if (len_duplicate % GROUP_LENGTH != 0)
        while (len_duplicate % GROUP_LENGTH != 0)
        {
            *duplicate++ = 'X';
            len_duplicate++;
        }
    *duplicate++ = '0';

    strcpy(msg, duplicate);
    free(duplicate);
    return msg;
}

```

---

### Post by Some Penguin on 2011-07-01
The address you're passing to free() isn't the address you got from malloc().

---

### Post by cdiem on 2011-07-01
> **Some Penguin said:**
> The address you're passing to free() isn't the address you got from malloc().

Thanks - reworked it to:

```

    char *duplicate, *begin;
    if ((begin = duplicate = malloc(strlen(msg) + 1)) == NULL)
        exit_error("Null duplicate string");
    ...
    free(begin);

```

But running the program still prints only a '\n' and nothing else. What am I missing?

EDIT: here's some debugging I was trying to do in gdb - not sure why duplicate doesn't seem to be updated (breakpoint is set right after allocating memory for duplicate):
```


(gdb) p msg
$1 = 0xbffff334 "Bla bla"
(gdb) p duplicate
$2 = 0x804b008 ""
(gdb) p *msg++
$3 = 66 'B'
(gdb) *duplicate++ = *msg++
Undefined command: "".  Try "help".
(gdb) p *duplicate++ = *msg++
$4 = 108 'l'
(gdb) p "%s",duplicate
$5 = 0x804b009 ""
(gdb) p *duplicate++ = '0'
$6 = 48 '0'
(gdb) p "%s",duplicate
$7 = 0x804b00a ""
(gdb) p msg
$8 = 0xbffff336 "a bla"
(gdb) p duplicate
$9 = 0x804b00a ""

```

---

### Post by Some Penguin on 2011-07-01
Check your parameters for strcpy, too.

---

### Post by cdiem on 2011-07-01
> **Some Penguin said:**
> Check your parameters for strcpy, too.

Thanks very much!

---

