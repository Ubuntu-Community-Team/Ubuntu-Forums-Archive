---
title: "#warning #error"
date: 2011-09-22
forum: Programming Talk
---

### Post by ankit3111 on 2011-09-22
#include<stdio.h>
#warning "This is warning."

void main()
{
	printf("Hello World.\n");
}

//filename example.c


----output -----
example.c:2:2: warning: #warning "This is warning."




Why is "#warning" tag repeating itself ... 
The same is the case with #error directive.
Thank you.

---

### Post by Beacon11 on 2011-09-22
I believe it's so you can differentiate between warnings and errors YOU write and warnings and errors actually tossed by the compiler.

---

### Post by trent.josephsen on 2011-09-22
Why not?

#warning is non-standard, so I'll address #error, which is defined in section 6.10.5 of the C99 standard as follows:

[quote=C99]
A preprocessing directive of the form
```
 # error *pp-tokens[opt]* *new-line*
```
causes the implementation to produce a diagnostic message that includes the specified sequence of preprocessing tokens.[/quote]

In other words, there's no constraints on what an #error directive may print, except that it must contain the tokens on the rest of the line.  It's perfectly reasonable, therefore, to display the entire line including the directive itself.

Why would you expect it to act differently?

Also, int main(void) not void main().  Get a better book.

---

