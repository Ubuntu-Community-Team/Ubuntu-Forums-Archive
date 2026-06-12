---
title: "Getting a double input?"
date: 2007-04-16
forum: Programming Talk
---

### Post by Lster on 2007-04-16
Everything's fine now: see later posts.

---

### Post by Wybiral on 2007-04-16
Yeah, you could probably just input a string and use atof to convert it to a double.

---

### Post by Xandei on 2007-04-16
I just whipped this up a test of your problem, and it seems to work just fine for me. :)

Edit: In hindsight I could have just said "try using %lf" but I didn't notice you only used %f. My mistake :)

Longer version: %f is the identifier for a float that scanf and printf use. %lf is a float with a modifier to indicate a wish for a double. At least with scanf, I'm a little hazy on its exact meaning for printf(), I think l is only valid with an int and specifys an unsigned long int. But libc doesnt seem too bothered either way with l or L.

```

#include <stdio.h>

int main( int argc, char* argv[] )
{
    double tD;

    printf("enter a double:\n");
    scanf("%lf", &tD);
    printf("%lf\n", tD);
}
```

g++ test.c -o Test

```

xander@Lyra:~/Code$ ./Test
enter a double:
5.666
5.666000

```

---

### Post by Lster on 2007-04-16
Thanks for the replies guys :).

All sorted...

---

