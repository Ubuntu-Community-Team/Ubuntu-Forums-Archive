---
title: "[SOLVED] GCC compiler warnings when using popen()"
date: 2008-04-10
forum: Programming Talk
---

### Post by dwhitney67 on 2008-04-10
Can someone help me resolve the following warnings?
```
test.c: In function ‘main’:
test.c:5: warning: implicit declaration of function ‘popen’
test.c:5: warning: initialization makes pointer from integer without a cast
test.c:22: warning: implicit declaration of function ‘pclose
```’
The man-page for *popen()* indicates that I need to include *stdio.h*, for which I have, and that* popen()* returns a *FILE* pointer.  What else could there be that I am missing?  Has* popen()* been deprecated?

Here's the code:
[PHP]
#include <stdio.h>

int main()
{
  FILE *pfd = popen( "ls -l", "r" );

  if ( pfd == 0 )
  {
    printf( "failed to open pipe\n" );
    return 1;
  }

  while ( !feof( pfd ) )
  {
    char buf[1024] = {0};

    fgets( buf, sizeof(buf) - 1, pfd );

    printf( "%s", buf );
  }

  pclose( pfd );

  return 0;
}
[/PHP]

---

### Post by heikaman on 2008-04-10
I've just compiled it on my box no warnings, i compiled with -Wall

---

### Post by heikaman on 2008-04-10
Just a crazy idea, check stdio.h file

---

### Post by dwhitney67 on 2008-04-10
I have my gcc command aliased to be "gcc -std=c99", and that is what is causing the warnings I am having.

Is it possible that the popen() and pclose() are deprecated in the C99 standards?

P.S.  I've decided to abandon the c99 standard, and rely on gnu89 standards.  The warnings are not showing up now.

---

### Post by scourge on 2008-04-10
> P.S. I've decided to abandon the c99 standard, and rely on gnu89 standards.

There's no need for that. Just replace '-std=c99' with '-std=gnu99'.


Also a couple of notes about your code:
1. You shouldn't use feof() to exit a loop: [http://www.gidnetwork.com/b-58.html](http://www.gidnetwork.com/b-58.html)
2. 'char buf[1024] = {0};' This is a weird way to initialize a char array. Most people would use "". In fact, there's no need to initialize it at all.
3. fgets() reads n-1 bytes, so you can just use sizeof(buf) without the subtraction.

---

### Post by dwhitney67 on 2008-04-10
Thanks... that works too!

---

