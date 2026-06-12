---
title: "C Dynamic argument passing"
date: 2009-01-15
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-15
I need to make a function with dynamic arguments, and pass all those dynamic args to printf

---

### Post by namegame on 2009-01-15
That's great. Is there anything we can help you with?

You need to ask a question. Otherwise, we could just be doing your homework...

---

### Post by Mr.Macdonald on 2009-01-15
This isn't homework, I am sitting at a high school trying to program a robot. And what kind of teacher assigns their kids to write a variable argument function. That isn't programming, it is busy work.

Assume my intentions are good before to throw a stone at me. I didn't write a full on request because this is so simple. But here is my question.

How does one write a variable argument function in C?

Please just answer so you don't waste mine nor your time!

---

### Post by Cracauer on 2009-01-15
```

  void craerr(int flags, int retval, const char *fmt, ...)
#ifdef __GNUC__
       __attribute__ ((format (printf,3,4)))
#endif
       ;

```
```


void craerr(int flags, int retval, const char *fmt, ...)
{
  va_list ap;
  if (fmt) {
    va_start(ap, fmt);
    vfprintf(stderr, fmt, ap);
    va_end(ap);
    fputc('\n',stderr);
  }
  if ( flags & CRAERR_PERROR ) {
    perror("System returned");
  }
[.... meat of function omitted]

```

---

### Post by Mr.Macdonald on 2009-01-15
I had a problem with include's

Here is the error that gcc spits out, the a's are from a network error (compiled on remote computer)
> In file included from test.c:2:
first/PPrinting.h:2:21: error: stdargs.h: No such file or directory
In file included from test.c:2:
first/PPrinting.h:7: error: expected â:â, â,â, â;â, â}â or â__attribute__â before â=â token
first/PPrinting.h: In function ârprintfâ:
first/PPrinting.h:16: error: âva_listâ undeclared (first use in this function)
first/PPrinting.h:16: error: (Each undeclared identifier is reported only once
first/PPrinting.h:16: error: for each function it appears in.)
first/PPrinting.h:16: error: expected â;â before âapâ
first/PPrinting.h:19: error: âapâ undeclared (first use in this function)
test.c: In function âmainâ:
test.c:5: error: âstruct <anonymous>â has no member named âMotorsâ

---

### Post by dwhitney67 on 2009-01-15
<stdarg.h> is what you need to include.

Example:
[php]
#include <stdio.h>
#include <stdarg.h>

void myPrintf(const char* format, ...);

int main()
{
  myPrintf("%s %d %d\n", "hello world", 10, 20);
  return 0;
}

void myPrintf(const char* format, ...)
{
  va_list args;
  va_start(args, format);

  vfprintf(stdout, format, args);

  va_end(args);
}
[/php]

---

