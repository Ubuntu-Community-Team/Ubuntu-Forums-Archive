---
title: "library for iconv.h"
date: 2009-05-23
forum: Programming Talk
---

### Post by quintok on 2009-05-23
I'm trying to compile against iconv.h but I'm not sure what symbolic object to link against.  libc6 has quite a few!

Thanks =)

---

### Post by snova on 2009-05-23
It looks to be part of libc. You don't have to link against anything (explicitly).

---

### Post by dwhitney67 on 2009-05-23
There are 3 functions defined in iconv.h; the implementation for these is presumably in /usr/lib/libc.a, and this static library is known to the linker.

Thus, for the program that appears below (which, btw I made up), you would compile/link as follows:
```

gcc my_iconv.c

```

Code for my_inconv.c:
```

#include <iconv.h>

int main()
{
  char*  inbuf        = 0;
  char*  outbuf       = 0;
  size_t inbytesleft  = 0;
  size_t outbytesleft = 0;

  iconv_t cd = iconv_open("foo", "morefoo");
  size_t  sz = iconv(cd, &inbuf, &inbytesleft, &outbuf, &outbytesleft);

  /* ... */

  iconv_close(cd);

  return 0;
}

```
I have never used iconv(), so if you have any questions related to it or iconv_open(), please post specific details.

---

### Post by quintok on 2009-05-24
Thank you both, I don't think iconv was what I was after having played with it a bit.
I have a library that outputs 8 bit ASCII (well technically UTF-8...) as a const char* and I'm trying to printf it.

I should explain.  I'm using libconfig to parse settings.cfg with ( in UTF-8 ) variables assigned.  one being copyright which is:
copyright = "Copyright";
now as per libconfig docs, it parses strings as 8 bit ASCII which is in this case I believe is analogous to UTF-8.  Linux's native character set is UTF-8 or at the very least my native character set is en-AU.UTF-8.  So I take libconfig's parsing of this UTF-8 string and print it.

At the moment I'm getting "&#65533;&#65533;right" instead of "Copyright" which seems odd to me as "&#65533;&#65533;" looks like it's a 16 bit representation of "Copy" but then it settles down and goes on with 8bit UTF-8 "right"

Here is the code in question:


Any help would be greatly appreciated.

nvm, must be my mistake somewhere... just tried to write a testcase and it worked.

---

