---
title: "Command Line"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by hiWorld on 2013-04-10
Could anyone tell me how to open executable file via terminal ??

Thanks for your feedback in advance!

---

### Post by tgalati4 on 2013-04-10
Change directory to where the file is located, add execute privileges if not green in the terminal.  Then run it:

```
cd directorywhereyourexecutableislocated
sudo chmod +x yourexecutable
./yourexecutable
```

These are precautions against files to run automatically which could be viruses.  So you have to take manual steps to run an executable.

---

### Post by hiWorld on 2013-04-10
[B]./main.cpp: line 3: $'\r': command not found
./main.cpp: line 4: using: command not found
./main.cpp: line 4: $'\r': command not found
./main.cpp: line 5: $'\r': command not found
./main.cpp: line 6: syntax error near unexpected token `('
'/main.cpp: line 6: `int main()
[/B]

Even though it's debugged and compiled terminal doesn't allow me to run it. Any suggestions ?

---

### Post by steeldriver on 2013-04-10
Compiling C++ creates a separate executable file - it does not make the source code file itself (the .cpp file) executable

You need to find THAT file and execute it - if you didn't specify a name for it on the compiler command line then it may have a default name such as 'a.out' e.g.

```
$ cat hello.cpp
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}
$
$ g++ hello.cpp
$
$ ./a.out
Hello World!
$ 
$ g++ -o hello hello.cpp
$
$ ./hello
Hello World!
$ 
```

---

### Post by hiWorld on 2013-04-10
Found it. It's located in the bin directory. Thank you for the quick response!

---

