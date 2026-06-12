---
title: "how to execute a c++ file"
date: 2006-06-16
forum: Programming Talk
---

### Post by IsKall on 2006-06-16
How do I execute a hello.cc file from the terminal?

It works perfectly from Anjuta but I want to learn to execute from the terminal too.

I tried all these:

```

gcc hello.cc
g++ hello.cc

gcc hello.o
g++ hello.o

```

but it doesn't show Hello World! (just a easy cout thing to see if the execution works in the terminal).

---

### Post by Jessehk on 2006-06-16
First, create a file (I'll call mine *hello.cpp*)

```

#include <iostream>

int main() {
    std::cout << "Hello, world!" << std::endl;
}

```

Then compile with

```

g++ hello.cpp -o hello

```

Run the executable with

```

./hello

```

:)

---

### Post by IsKall on 2006-06-16
I know how to program ;) I am just new to program in linux enviroment. :)

Thank you for the help Jessehk!

---

### Post by IsKall on 2006-07-29
how do I compile multiple .cc and a .h files together?

---

### Post by Lord Illidan on 2006-07-29
You need **makefiles** for that. Google up some tutorials..I never made one myself.

---

### Post by IsKall on 2006-07-29
okey, will look for that :)

---

### Post by nagilum on 2006-07-30
A Makefile is the right choice for a project with multiple source files, you might even want to use autoconf and automake which will create the Makefile for you.
Although for quick testing this is overkill, just compile them like in the example above:
```

g++ -o hello hello.cpp world.cpp

```
Alternatively you can also compile the files separately and link them together as a last step:
```

g++ -c hello.cpp  # produces hello.o
g++ -c world.cpp
g++ -o hello hello.o world.o

```

---

### Post by X.Cyclop on 2006-08-01
It's easier using the best IDE [Code::Blocks]("http://forums.codeblocks.org/index.php?board=20.0"). ;)

---

