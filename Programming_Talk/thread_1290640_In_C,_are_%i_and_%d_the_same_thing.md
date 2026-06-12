---
title: "In C, are %i and %d the same thing?"
date: 2009-10-13
forum: Programming Talk
---

### Post by jessiebrownjr on 2009-10-13
Title says my question.. I'm reading C for dummies, and he pulled a switch on me. I made a sample program to find out the limitations of what I can put in %d/%i and it does "seem" to be the same, but is it?

Try googling C + %i lol, I tried, failed hardcore... He didn't document anything about %i he just started using it in the book, help? :-)

---

### Post by NovaAesa on 2009-10-13
Do you mean % as in modulo or the % used in format strings?

---

### Post by jessiebrownjr on 2009-10-13
> **NovaAesa said:**
> Do you mean % as in modulo or the % used in format strings?

```

#include <stdio.h>
int main()
{
printf("Rawr %d.\n",55)
return (0);
}

```

---

### Post by sloggerkhan on 2009-10-13
[http://www.cplusplus.com/reference/clibrary/cstdio/fprintf/](http://www.cplusplus.com/reference/clibrary/cstdio/fprintf/)
Based on above link, %i and %d are the same.

---

### Post by jessiebrownjr on 2009-10-13
Appreciate it, this dude that wrote this version of C for dummies is a twit.. terrible sense of humor and sloppy code.. even I can tell its sloppy! lol

---

