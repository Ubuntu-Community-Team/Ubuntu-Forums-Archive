---
title: "printf a return value?"
date: 2008-02-26
forum: Programming Talk
---

### Post by S15_88 on 2008-02-26
quick question how to you printf a return value.  i'm having a total mental block haha

lets say i have the funtion fseek() that seeks to some point in a binary file then call ftell() to find the current position.  how would i print out the return value of ftell()?

Thanks, ALain

---

### Post by mike_g on 2008-02-26
Just call it inside the printf. Something like:

         printf("%d", ftell(file));

---

### Post by Martin Witte on 2008-02-26
by using google :), first hit for ftell: [http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html](http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html)

---

### Post by Lster on 2008-02-26
ftell is apparently defined like this:

[PHP]long int ftell ( FILE * stream );[/PHP]

The printf function:

[QUOTE=C++ Reference]Writes to the standard output (stdout) a sequence of data formatted as the format argument specifies. After the format parameter, the function expects at least as many additional arguments as specified in format.[/QUOTE]

and is defined:

[PHP]int printf ( const char * format, ... );[/PHP]

See the printf link below for further reference on printf and how to print certain data.

Sources:
[http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html](http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html)
[http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)

I haven't had time to go into any details. Is you still have problems do post back and I can help you you further. :)

---

