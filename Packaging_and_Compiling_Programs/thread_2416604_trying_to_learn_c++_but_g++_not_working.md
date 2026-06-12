---
title: "trying to learn c++ but g++ not working"
date: 2019-04-12
forum: Packaging and Compiling Programs
---

### Post by rev-matthewagilmore on 2019-04-12
#include <iostream>
using namespace std;

int main() 
{
    cout << "Hello, World!";
    return 0;
}

usero@usero-desktop:~$ g++ hi.h -o hi
usero@usero-desktop:~$ ./hi
bash: ./hi: Permission denied
usero@usero-desktop:~$ chmod +x hi
usero@usero-desktop:~$ ./hi
bash: ./hi: cannot execute binary file: Exec format error
sero@usero-desktop:~$ uname -a
Linux usero-desktop 4.18.0-17-generic #18~18.04.1-Ubuntu SMP Fri Mar 15 15:27:12 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by TheFu on 2019-04-12
g++ compiles .cpp, .cxx, .C files, not .h files.

It looks like you just named the file wrong.  .h ----> .cpp

You might want to append an "<< endl;" to the cout as well. You'll see.

---

### Post by spjackson on 2019-04-12
> **rev-matthewagilmore said:**
> 
usero@usero-desktop:~$ g++ hi.h -o hi

For any given input file, the file name suffix determines what kind of compilation is done by the g++ command. The action it performs by default for .h files is to create a GCC precompiled header. So that's what the above command is doing. You can tell g++ that you are using unconventional file name suffixes and want your source to be treated differently by using the -x option, e.g.
```

g++ -x c++ hi.h -o hi

```
Here "-x c++" indicates that hi.h is not a header file as its suffix implies but is in fact a c++ source file. However, it would be far better to use conventional file name suffixes as per TheFu's answer.

---

