---
title: "Compiling very basic c++ program, need help."
date: 2010-10-23
forum: Packaging and Compiling Programs
---

### Post by louislepperd on 2010-10-23
Hi,
I'm keen to start trying to code some c++ on linux, I've done some programming in C for some nxt robots before.
I was following a tutorial online and I'm trying to compile hello world.
code:

```

\* 0001_hello.cpp *\
#include <iostream>
using namespace std;
int main()
{
     cout << endl << "Hello, Happy programming";
     return 0;
}

```

I'm trying to compile it with this command here:
```

g++ -Wall -g -o hello.out hello.cpp 

```

This is the error I'm getting:
```

hello.cpp:1: error: stray ‘\’ in program
hello.cpp:1:4: error: invalid suffix "_hello.cpp" on integer constant
hello.cpp:1: error: stray ‘#’ in program
hello.cpp:1: error: expected unqualified-id before numeric constant
hello.cpp:1: error: expected constructor, destructor, or type conversion before numeric constant
hello.cpp: In function ‘int main()’:
hello.cpp:6: error: ‘cout’ was not declared in this scope
hello.cpp:6: error: ‘endl’ was not declared in this scope

```
I get the feeling that I'm supposed to have an iostream library somewhere or something like that, but I have no idea.
(hello.cpp is in a folder with nothing else in it)

Can someone help?

Thanks
Louis

---

### Post by SevenMachines on 2010-10-23
Comments dont use backslashes, ie
> /* This is a comment */
// so is thisSo this...
> \* 0001_hello.cpp *\should be this,
> /* 0001_hello.cpp */

---

### Post by louislepperd on 2010-10-23
Thank you very much, that fixed it.

---

