---
title: "Unable to access #defines from #included header!"
date: 2009-08-19
forum: Programming Talk
---

### Post by marlinman on 2009-08-19
Greetings

When I try to 'gcc' (using U9.04) the following short file

-------------------------------------
#include <stdio.h>
#include <limits.h>

int main()
{
 printf("%llu\n",ULLONG_MAX);
 return 0;
}
-------------------------------------

I get the message "error: 'ULLONG_MAX' undeclared (first use in this function)". Yet on inspecting limits.h (there are a few - I'm guessing the relevant one is in usr/lib/gcc/i486-linux-gnu/4.3/include-fixed) I see a #define for ULLONG_MAX:confused: (Also looked at limits.h in /usr/include and found the value defined there too...).

Any suggestions as to what's going on appreciated!

---

### Post by Arndt on 2009-08-19
> **marlinman said:**
> Greetings

When I try to 'gcc' (using U9.04) the following short file

-------------------------------------
#include <stdio.h>
#include <limits.h>

int main()
{
 printf("%llu\n",ULLONG_MAX);
 return 0;
}
-------------------------------------

I get the message "error: 'ULLONG_MAX' undeclared (first use in this function)". Yet on inspecting limits.h (there are a few - I'm guessing the relevant one is in usr/lib/gcc/i486-linux-gnu/4.3/include-fixed) I see a #define for ULLONG_MAX:confused: (Also looked at limits.h in /usr/include and found the value defined there too...).

Any suggestions as to what's going on appreciated!

The definition in limits.h is within an #ifdef, with the comment /* ISO C99 */. So this symbol didn't exist before C99, and you need to tell gcc that C99 is what you want:

```
gcc -std=c99 -c file.c
```

---

### Post by dwhitney67 on 2009-08-19
From what I was able to deduce, ULLONG_MAX is only defined for the 1999 ISO C standard, not the 1989 standard.

Thus, compile your program such as:
```

gcc -std=gnu99 myprog.c

```
Alternatively, you can try using:
```

gcc -std=c99 myprog.c

```
There are subtle differences between gnu99 and c99.

---

### Post by marlinman on 2009-08-19
Ahh that's the problem! For some reason, I was under the impression I had to force C89 compliance, not C99!

Alas, the value reported is kind of small. I'm running an x86 OS - would this be why? According to

[http://home.att.net/~jackklein/c/inttypes.html](http://home.att.net/~jackklein/c/inttypes.html)

I should expect 9223372036854775807, whereas 4294967295 is all I get (which is the same as is reported for ULONG_MAX).

---

### Post by dwhitney67 on 2009-08-19
That's odd... I get this number:  18446744073709551615

P.S.  The number above is equivalent to 2^64 - 1.

---

### Post by Arndt on 2009-08-19
> **dwhitney67 said:**
> That's odd... I get this number:  18446744073709551615

So do I. What does the -E option give? It shows the source code after preprocessing.

For me, it does this somewhat funny thing:

```
int main()
{
printf("%llu\n",(9223372036854775807LL * 2ULL + 1ULL));
return 0;
}
```

---

### Post by marlinman on 2009-08-19
Whoops - rereading the page I linked, that is indeed the number I should expect dwhitney67 :-)

---

### Post by marlinman on 2009-08-19
Arndt - ULLONG_MAX is replaced by that very thing on my sys too!

Edit: Gah - problem solved. Using that second command you suggested dwhitney67 resulted in a.out, which force-of-habit saw me attempt to execute by typing the name of my source file (sans ".c"). Executing a.out gives me 18446744073709551615, which I've been after for some time!

Thanks for the help :-)

---

### Post by Arndt on 2009-08-19
> **marlinman said:**
> Arndt - ULLONG_MAX is replaced by that very thing on my sys too!

I have a 64 bit CPU, I don't know if that's supposed to make a difference. If C99 has unsigned long long, it ought to support it too. What does the code below print?

```
#include <stdio.h>
#include <limits.h>

int main()
{
  printf("%lu\n", sizeof(unsigned long long));

}
```

---

### Post by marlinman on 2009-08-19
All's well now thx Arndt - see my last (edited) post :-)

---

