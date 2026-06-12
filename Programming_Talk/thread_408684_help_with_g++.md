---
title: "help with g++"
date: 2007-04-13
forum: Programming Talk
---

### Post by spzentz on 2007-04-13
Hi,
I have installed the package that includes g++. The compiler will compile c++ files but I cannot run the executable (in the terminal). It always says command not found.
Any help is apreciated.
Thanks

---

### Post by tino27 on 2007-04-13
This is probably due to the directory not being in your path. When in the same directory as the executable, try prefixing the name with "./". (without the quotes) to refer to the cwd.

---

### Post by WW on 2007-04-13
Did you remember to put ./ in front of the executable?

Example: This is hello.cpp:
```

#include <iostream>

using namespace std;

int main()
    {
    cout << "Hello, World!\n";
    return 0;
    }

```
Compile and run:
```

$ g++ hello.cpp -o hello
$ ./hello
Hello, World!
$

```

---

### Post by spzentz on 2007-04-13
Yes, I didn't realise that I needed the ./ before the executable.
Thanks for all the help.

---

