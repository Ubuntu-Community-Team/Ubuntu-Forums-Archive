---
title: "strcat in C"
date: 2006-08-25
forum: Programming Talk
---

### Post by Lster on 2006-08-25
Hi

How can I concatenate 2 char*s. The following code doesnt work:

...

I am compiling using GCC.

Thanks

---

### Post by toojays on 2006-08-25
There is a bug here: the way you have defined a and b mean that each only has 4 bytes of storage. But to store the result, you need at least 7 bytes of storage.

For instance:```

#include <string.h>
#include <stdio.h>

int main(){
  char a[7] = "abc";
  char * b = "xyz";
  strcat(a, b);
  printf("%s\n", a);
  return 0;
}
```

The GNU project has some really good documentation about the standard C library. I suggest you start at [String and Array Utilities](http://www.gnu.org/software/libc/manual/html_node/String-and-Array-Utilities.html).

This documentation is in the package glibc-doc, once you install that, you can access it quickly from Emacs with "C-h i m libc RET", or slowly  by using System->Help->System Documentation, select "Command Line Help" (down the bottom of the page), "GNU Info Pages", "GNU libraries" (with a lowercase l, as opposed to "GNU Libraries") then "Libc". Phew!

---

### Post by LordHunter317 on 2006-08-25
Ignoring that, you're not allowed to overwrite a constant string anyway.

---

### Post by JonahRowley on 2006-08-26
Do not use strcat.  The strcat function is dangerous as it does no bounds checking.  Always use functions with bounds checking, in this case, you probably want strncat.  And yes, strcat can be safe if you do the bounds checking yourself, but that complicates things and future edits can introduce bugs.  Just use the functions with bounds checking and stay on the safe side.  It's a good habit to get into from the beginning.

Some would argue not touching C is a good habit as well ;)

---

