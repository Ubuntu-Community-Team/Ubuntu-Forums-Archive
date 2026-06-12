---
title: "gcc cannot find libraries?"
date: 2010-04-11
forum: Programming Talk
---

### Post by starshape on 2010-04-11
Hi.
I have files, written in C: 
something.h and something.c containing function f()
i compile them with command:

gcc -c something.c -o something.o

and pack them into a library:

ar r libsth.a something.o

I also have a file main.c, in which i use this function f(), and in this file I have a line: #include "something.h"

Then, when i try to compile main.c, with command:

gcc main.c -o main -L. -lsth

I get an error:
something.h: No such file or directory.

I can't understand why? I also tried to provide full path to the library for -L, but that didn't work either (although, I could've done that wrong). I also tried including -I. in command but that also didn't work.

Oh, and I think the files are correct - when I don't include this library, instead just leave this files something.h and something.c in the directory, program compiles just fine.

All those files are in the same directory, somewhere in my home directory

---

### Post by Compyx on 2010-04-11
Did you by any chance use #include <something.h>? Replace with "something.h".
Including files with <> is reserved for system headers (those in /usr/include/*), while including with "" is used for non-system headers, such as your own.

I just set up a situation as you described, and with <something.h> I get the 'no such file' error, while using "something.h" everything works as expected.

Hope this helps.

---

### Post by starshape on 2010-04-11
As I said, i used #include "something.h". Doesn't work. But thanks :)

---

### Post by pbrane on 2010-04-11
The error you're getting in a compiler error, not a linker error.
Try adding **-I.**
```

gcc main.c -o main -L. -lsth -I.

```

---

### Post by Compyx on 2010-04-12
You might want to post your code, along with the commands you use to compile and the output of gcc. Not much use guessing what's happening.

---

