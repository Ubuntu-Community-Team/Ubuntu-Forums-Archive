---
title: "glibc stdlib C implementation question"
date: 2011-03-08
forum: Programming Talk
---

### Post by Houman on 2011-03-08
hi guys;

I just downloaded the glibc 2.13 implementation and I was snooping around and I was looking at some of the function definitions. There is something that I dont quite understand. 

For example if you look at the implementation of strcpy you get:

```

char *
strcpy (dest, src)
     char *dest;
     const char *src;
{
  reg_char c;
  char *__unbounded s = (char *__unbounded) CHECK_BOUNDS_LOW (src);
  const ptrdiff_t off = CHECK_BOUNDS_LOW (dest) - s - 1;
  size_t n;

  do
    {
      c = *s++;
      s[off] = c;
    }
  while (c != '\0');

  n = s - src;
  (void) CHECK_BOUNDS_HIGH (src + n);
  (void) CHECK_BOUNDS_HIGH (dest + n);

  return dest;
}

```

I have no idea what is the meaning of the variables that come after the function definition:

```

char *dest;
const char *src; 

```
why arnt these defined in the typical way inside the argument list?


thanks

Houman

---

### Post by trent.josephsen on 2011-03-08
The "typical way" you refer to is known as prototyping and it didn't exist prior to ANSI (C89).  Old-style definitions like the one you posted are still pretty common in codebases that go back to the '90s and before.

I'd like to note that just because the definition doesn't include a prototype doesn't mean it can never have a prototype.  In your own C files you can prototype it appropriately and use it as if it were declared with the new-style definition; this is why header files exist (and one reason we don't #include source files).

---

### Post by Houman on 2011-03-08
thank you Trent;
that clears things up alot :)

H

---

