---
title: "help with getline and sscanf"
date: 2010-11-04
forum: Programming Talk
---

### Post by c2tarun on 2010-11-04
is it possible to read "P 6 5" using getline and separate 'P',6,5 in three variables one character and two integer using sscanf???
if yes please tell me how to do this.

---

### Post by schauerlich on 2010-11-04
Use fgets to read in a line, and strtok to split the line on each space.

---

### Post by johnl on 2010-11-04
```

#define _GNU_SOURCE /* for getline */
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(int argc, char* argv[])
{
    size_t size = 128;
    char*  line = malloc(size);
    
    ssize_t len = getline(&line, &size, stdin);    
    /* you should do some error checking on the
     * return value of getline here. */

    char c;
    int i, j;

    /* sscanf() returns the number of items successfully read */
    if (sscanf(line, "%c %d %d", &c, &i, &j) != 3) {
        printf("didn't get all three values\n");
    } else {
        printf("read %c, %d, and %d\n", c, i, j);
    }

    free(line);
    
    return 0;
}

```

---

### Post by trent.josephsen on 2010-11-04
> **schauerlich said:**
> Use fgets to read in a line, and strtok to split the line on each space.
This.  There's no reason to use a non-standard extension (getline) and a procedure for reading formatted strings (sscanf) to get input from the user.  Problems like this are what strtok was made for.

---

### Post by schauerlich on 2010-11-04
The problem with using the scanf family is that when it fails, it can fail epically. It's much safer to read in a line at a time, and then parse it manually with strtok. This is especially easy with a simple example like this.

---

### Post by johnl on 2010-11-04
> **schauerlich said:**
> The problem with using the scanf family is that when it fails, it can fail epically. It's much safer to read in a line at a time, and then parse it manually with strtok. This is especially easy with a simple example like this.

I think in this case I would use **fgets** and then **sscanf**.  There's no advantage to using strtok in this situation.

I would never use plain **scanf** to read user input.  But could you provide an example of sscanf "failing epically?"   I would rather use sscanf than mess around with tokenising and converting with strtok.  Especially since there are some issues with strtok, such as (from the man page: )

```

* These functions modify their first argument.
* These functions cannot be used on constant strings.
* The identity of the delimiting character is lost.
* The strtok() function uses a static buffer while parsing, so it's not
    thread safe.  Use strtok_r() if this matters to you.

```

You can use strtok_r to avoid the last issue, but strtok_r is not part of the C standard like strtok.

---

### Post by trent.josephsen on 2010-11-04
The problem with sscanf in this situation is that you can't use it to read the input at all unless the input matches the format string exactly.  If I
```
sscanf(line, "%c %d %d", &c, &i, &j);
```
and type "foo 2 3", it will fail, giving me no information as to what went wrong apart from the useless fact that 0 fields could be read.  At this point I can either discard the input entirely, as scanf does, or else fall back on using strtok or a similar method, which I should have done in the first place.

In a nutshell, scanf and friends simply do not give enough information.  It makes sense to use them only when you **know** the format of the input and don't care about input that is not in that format.  In some cases, it's acceptable to say "I didn't understand that line; therefore, I'm going to ignore it entirely".  Interactive user input is not one of those cases.

---

### Post by c2tarun on 2010-11-06
thanx a lot evryone.:)

---

