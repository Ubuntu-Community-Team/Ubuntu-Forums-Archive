---
title: "C/c++"
date: 2010-05-04
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-05-04
Is it normal that strcmp() in Linux doesn't give the same result as in windows ? 
for example 
in windows for given strings it gives -1 
while with Ubuntu is returns -97 
Both are negative but how do they differ ?

---

### Post by MadCow108 on 2010-05-04
because its allowed by the standard:
[http://www.opengroup.org/onlinepubs/000095399/functions/strcmp.html](http://www.opengroup.org/onlinepubs/000095399/functions/strcmp.html)
> 
Upon completion, strcmp() shall return an integer greater than, equal to, or less than 0, if the string pointed to by s1 is greater than, equal to, or less than the string pointed to by s2, respectively.

no mention of what exactly is returned (except type and sign)
its up to the implementation
So there will often be differences between platforms
on mine it also only returns -1, 0, +1

---

### Post by lisati on 2010-05-04
It could be a subtle difference in the implementation. 

AFAIK (I haven't done much programming in C or C++) what is important is the sign of the returned value, rather than the exact value.

[http://www.cplusplus.com/reference/clibrary/cstring/strcmp/](http://www.cplusplus.com/reference/clibrary/cstring/strcmp/)

---

### Post by pbrane on 2010-05-04
This is the description from the man pages:
       The  strcmp()  function compares the two strings s1 and s2.  It returns
       an integer less than, equal to, or greater than zero if  s1  is  found,
       respectively, to be less than, to match, or be greater than s2.

Here is the source:
```

/* Copyright (C) 1991, 1996, 1997, 2003 Free Software Foundation, Inc.
   This file is part of the GNU C Library.

   The GNU C Library is free software; you can redistribute it and/or
   modify it under the terms of the GNU Lesser General Public
   License as published by the Free Software Foundation; either
   version 2.1 of the License, or (at your option) any later version.

   The GNU C Library is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
   Lesser General Public License for more details.

   You should have received a copy of the GNU Lesser General Public
   License along with the GNU C Library; if not, write to the Free
   Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
   02111-1307 USA.  */

#include <string.h>
#include <memcopy.h>

#undef strcmp

/* Compare S1 and S2, returning less than, equal to or
   greater than zero if S1 is lexicographically less than,
   equal to or greater than S2.  */
int
strcmp (p1, p2)
     const char *p1;
     const char *p2;
{
  register const unsigned char *s1 = (const unsigned char *) p1;
  register const unsigned char *s2 = (const unsigned char *) p2;
  unsigned reg_char c1, c2;

  do
    {
      c1 = (unsigned char) *s1++;
      c2 = (unsigned char) *s2++;
      if (c1 == '\0')
        return c1 - c2;
    }
  while (c1 == c2);

  return c1 - c2;
}
libc_hidden_builtin_def (strcmp) 

```
Maybe you can find a copy of the windows standard C lib and compare

---

### Post by cap10Ibraim on 2010-05-04
I noticed that unlike my windows here on ubuntu it compute the total difference 
example : 
               strcmp("abe","abc")    return 2 
               strcmp("abc","abe")    return -2

---

### Post by dwhitney67 on 2010-05-04
> **cap10Ibraim said:**
> I noticed that unlike my windows here on ubuntu it compute the total difference 
example : 
               strcmp("abe","abc")    return 2 
               strcmp("abc","abe")    return -2

Which Ubuntu are you running?

I get 1 and -1, respectively, when I test with your strings.

```

#include <stdio.h>
#include <string.h>

int main(void)
{
   const char* str1 = "abe";
   const char* str2 = "abc";

   printf("strcmp(\"%s\", \"%s\") = %d\n", str1, str2, strcmp(str1, str2));
   printf("strcmp(\"%s\", \"%s\") = %d\n", str2, str1, strcmp(str2, str1));

   return 0;
}

```

---

### Post by cap10Ibraim on 2010-05-04
Ubuntu Lucid Lynx 10.04 64bit

---

### Post by juzzlin on 2010-05-04
> **cap10Ibraim said:**
> I noticed that unlike my windows here on ubuntu it compute the total difference 
example : 
               strcmp("abe","abc")    return 2 
               strcmp("abc","abe")    return -2


I tried this code on Lucid Lynx:

#include <iostream>
#include <cstring>

int main()
{
    std::cout << strcmp("abe","abc") << std::endl;
    std::cout << strcmp("abc","abe") << std::endl;
    return 0;
}

..and it returns 1 and -1.

---

### Post by cap10Ibraim on 2010-05-04
> **juzzlin said:**
> I tried this code on Lucid Lynx:
..and it returns 1 and -1.
64bit or 32bit ?

---

### Post by juzzlin on 2010-05-04
> **cap10Ibraim said:**
> 64bit or 32bit ?

32-bit.

---

