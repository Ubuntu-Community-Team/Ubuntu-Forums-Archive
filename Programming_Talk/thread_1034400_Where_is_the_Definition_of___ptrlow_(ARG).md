---
title: "Where is the Definition of __ptrlow (ARG)?"
date: 2009-01-08
forum: Programming Talk
---

### Post by huangyingw on 2009-01-08
Hello all:
    I am a beginner at Ubuntu. I have downloaded the Glibc 2.2.5 source code and begin reading. 
    The final of the thread is the source code of  “strcpy”. And I am trying to expand all the related macros in code.
Much of the macro realizations have been found, except this headache one "__ptrlow (ARG)". Wherever else should I search? Or is there any other source 
code which I am missing?
   Also, could someone be kind to provide me with a “find“ cmd to search a key word within the forest of codes?
   I am expecting a cmd like this one: 
find /media/storage/programming/ -name "makefile" -o -name "*.c" -o -name "*.cc" -path "/media/storage/" -prune> /media/storage/programming/shell/find.log
=================================================================
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
=================================================================

---

### Post by Zugzwang on 2009-01-08
Look here: [http://ftp.softnet.tuc.gr/pub/gnu/www/software/gcc/projects/bp/main.html](http://ftp.softnet.tuc.gr/pub/gnu/www/software/gcc/projects/bp/main.html)

It looks like this is an operator of the GCC.

---

### Post by AnRa on 2009-01-08
> **huangyingw said:**
> could someone be kind to provide me with a “find“ cmd to search a key word within the forest of codes?
[grep](http://manpages.ubuntu.com/manpages/hardy/en/man1/grep.1.html)

---

### Post by huangyingw on 2009-01-09
> **Zugzwang said:**
> Look here: [http://ftp.softnet.tuc.gr/pub/gnu/www/software/gcc/projects/bp/main.html](http://ftp.softnet.tuc.gr/pub/gnu/www/software/gcc/projects/bp/main.html)

It looks like this is an operator of the GCC.

Yes, this link tell me something about Bounds checking. But it doesn't tell me where could I found the realization of __ptrlow (ARG). Could you provide me more clues?

---

