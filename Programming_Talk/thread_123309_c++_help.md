---
title: "c++ help"
date: 2006-01-29
forum: Programming Talk
---

### Post by jon_z on 2006-01-29
jon@Electra:~$ gcc -c helllo.C
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from helllo.C:1:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.


just wondering what i can do to fulfil the missing .h files...ive tried numerous packages.

---

### Post by Adrian on 2006-01-29
[QUOTE=jon_z]
just wondering what i can do to fulfil the missing .h files...ive tried numerous packages.[/QUOTE]

Have you tried
```
#include <iostream>
```
?

---

### Post by jon_z on 2006-01-29
no go

---

### Post by Adrian on 2006-01-29
[QUOTE=jon_z]no go[/QUOTE]

Well, that should work. I'm out of ideas already :)

---

### Post by jerome bettis on 2006-01-29
iostream is a c++ thing and you're writing a C file & using a C compiler.

```
#include <stdio.h>

int main(int argc, char* argv[])  {
    printf("Hello World!\n");
    return 0;
}
```

---

### Post by Adrian on 2006-01-29
[QUOTE=jerome bettis]iostream is a c++ thing and you're writing a C file & using a C compiler.[/QUOTE]

True, I didn't notice the use of gcc.

Since the topic says C++ help, I assume that the intention is the write a C++ program. Then **g++** must be used for compiling instead of **gcc**.

---

### Post by jon_z on 2006-01-30
thank you very very much, solved the problem :-) simple error by me

---

