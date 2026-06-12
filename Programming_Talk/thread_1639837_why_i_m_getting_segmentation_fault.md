---
title: "why i m getting segmentation fault???"
date: 2010-12-07
forum: Programming Talk
---

### Post by c2tarun on 2010-12-07
when i m executing this:
```


#include<stdio.h>

int main(void)
{
  char* p = "hello world";
  p[0]='H';
  printf("%c\n",p[0]);
}


```

i m getting segmentation fault.
but when i m running this:

```


#include<stdio.h>

int main(void)
{
  char* p = "hello world";
//  p[0]='H';
  printf("%c\n",p[0]);
}


```
its giving me expected output.

why so??

---

### Post by GeneralZod on 2010-12-07
p is a pointer to the string literal "hello world", which is (generally) stored in read-only memory - or at least, any attempt to modify it leads to undefined behaviour, in this case a crash.

```

p[0] = 'H';

```

represents an attempt to modify the first character in this string literal.

---

### Post by r-senior on 2010-12-07
This has come up before. There's a subtle difference between what you have and this, which works:

```

#include<stdio.h>

int main(void)
{
  char p[] = "hello world";
  p[0] = 'H';
  printf("%c\n", p[0]);
}

```

The difference being that the above initialises a string with a literal rather than creating a pointer to an immutable string literal.

---

### Post by c2tarun on 2010-12-07
thanks

---

### Post by owiknowi on 2010-12-07
The technical information I have on this comes from using ArcView (GIS-application):
An application is trying to access a memory address which is already in use by another process or application.
For example a mail program is running in the background.

Usually I quit all other applications (especially those who consume lots of memory- and systemresources) an restart only the application I really need.

Sad but true: for some applications multitasking is something they do elsewhere...

Addendum
See that my answer probably is not what you wanted to know. Sorry.

---

