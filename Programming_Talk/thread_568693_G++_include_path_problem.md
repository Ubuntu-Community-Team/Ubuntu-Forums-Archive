---
title: "G++ include path problem"
date: 2007-10-06
forum: Programming Talk
---

### Post by statusquo on 2007-10-06
Hi,

I'm trying to compile a program that uses a utility called wordnet. I need to use its header file, which is located at /usr/local/WordNet-3.0/include/wn.h

My code is in a file called main.cpp looks like this:

```
#include <iostream>
#include "wn.h"

int main() {

  // yadyada

}
```

And I'm trying to compile with:

g++ -l/usr/local/WordNet-3.0/include/ -o main main.cpp

Yet for some reason it gives:

main.cpp:3:24: error: wn.h: No such file or directory

If I add #include "/usr/local/WordNet-3.0/include/wn.h" then it works perfectly, but I don't want to do this because then I won't be able to use my code on any other computers.

I'm using:
g++ (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Does anyone have any idea why this might be happening?

Thanks

---

### Post by Compyx on 2007-10-06
You're using an 'el', not a capitalized 'i': 'I', which is rather hard to distinguish in some fonts.
So basically you're telling g++ to link with the library '/usr/local/WordNet-3.0/include/', which doesn't make much sense.

---

### Post by statusquo on 2007-10-06
Doh! I can't believe I wasted almost an hour on that. But thanks a bunch for the help.

---

### Post by Compyx on 2007-10-06
You're welcome.

---

### Post by ekricyote on 2009-01-26
So how does g++'s linker determine which directories to search for the libraries? Does it depend on $PATH or use another method?

While we're on the topic of libraries, I know there is a standard lib{libname}.so format for shared libraries; is there a standard convention for static libs or are they just built into output executables?

---

### Post by snova on 2009-01-26
This is a pretty old thread, you'd have been better off creating a new one...

> **ekricyote said:**
> So how does g++'s linker determine which directories to search for the libraries? Does it depend on $PATH or use another method?

I think there are a few directories built in (defined in an obscure config file, actually) that it searches. Then it additionally searches directories you specify on the command line with the -L flag, that is, **-L/directory/to/search**

> While we're on the topic of libraries, I know there is a standard lib{libname}.so format for shared libraries; is there a standard convention for static libs or are they just built into output executables?

Static libraries typically have an .a extension (a for ar, the tool used to create them, I guess).

---

