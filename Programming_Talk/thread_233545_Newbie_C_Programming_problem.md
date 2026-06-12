---
title: "Newbie C Programming problem"
date: 2006-08-10
forum: Programming Talk
---

### Post by pez on 2006-08-10
Hi, I was wondering if someone could tell me why I am having problems with this code:

```
#include <stdio.h>
/* count characters in input; 1st version */
main()
{
    long nc;
    nc = 0;
    while (getchar() != EOF)
        ++nc;
    printf("%ld\n", nc);
}
```

```

gcc -o test test.c
./test
```

I inputted 'test' and hit enter but all that happens is do a carriage return and doesn't represent EOF. 

I'm banging my head here!

---

### Post by jayemef on 2006-08-10
I didn't test your code, but EOF is Ctrl+D, not Enter.

Hope that helps...

---

### Post by moma on 2006-08-10
Already told by "jayemef".

^d (CNTR + D) represents EOF.
Note that it will also count all CRs (ENTER keys).

---

### Post by pez on 2006-08-10
Yes, that did work. Thank you very much! I actually have to hit CTR+D twice for it to assert EOF - is this correct?

---

### Post by moma on 2006-08-11
Output from getchar() is buffered, so you must enter [RETURN] before it outputs anything. 
Double ^D has to do with that buffer.

Google for "getche + linux"

Or take a look at this code that sets STDIN in non-buffered mode.
[http://www.vivaolinux.com.br/dicas/verDica.php?codigo=1663]("http://www.vivaolinux.com.br/dicas/verDica.php?codigo=1663")
Requires 
#include <unistd.h>
#include <termios.h>

---

