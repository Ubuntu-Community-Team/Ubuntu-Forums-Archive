---
title: "Getting C++ IDE working"
date: 2012-02-28
forum: Programming Talk
---

### Post by JC75 on 2012-02-28
[LEFT]Hi, I'm a little new to Linux/Ubuntu and have been trying to set up a C++  IDE.  I'm using Ubuntu 11.10, and have tried two of the more popular  IDEs: Code::Blocks and Geany. So far they have resulted with the same  error, however. 
When I put in the simple code: 
#include <iostream> using namespace std;  int main () {   cout << "Hello World!";   return 0; }

It comes up with:
2: using: not found
4: Syntax error: "(" unexpected 

How should I fix this?





[/LEFT]

---

### Post by stchman on 2012-02-28
That program runs fine.  Please wrap your code in ```
 tags.

[CODE]
#include <iostream>
using namespace std;
int main() { 
    cout << "Hello World!\n";
    return 0;
}

```

---

### Post by r-senior on 2012-02-29
I'd suggest getting that program working from the command line first to take the IDE setup out of the equation:

```
$ cat hello.cpp
#include <iostream>
using namespace std;
int main() { 
    cout << "Hello World!\n";
    return 0;
}
$ g++ -o hello hello.cpp
$ ./hello
Hello World!

```

In other words, make a file called hello.cpp containing that program (or call it hello.cc if you prefer). Compile with the g++ command shown above and run with './hello'.

---

### Post by Some Penguin on 2012-02-29
> **JC75 said:**
> 
2: using: not found


...what did you name the program?  something.c, perchance, instead of .cpp / .cc?

---

### Post by r-senior on 2012-02-29
That was my first thought, but I tried it and got:

```
$ gcc -o hello hello.c
hello.c:1:20: fatal error: iostream: No such file or directory
compilation terminated.

```

---

### Post by Vaphell on 2012-02-29
do you have build-essential installed?
iostream is c++ header so it should be g++ -o hello hello.cpp

---

### Post by Zugzwang on 2012-02-29
@JC75: The error message suggest that you are trying to execute your C++ program as a Shell script. Make sure that you save it to a file with the ending .cpp (or .C with capital C), and that your IDE recognises the whole setting as a C++ program, so that it compiles the program before execution. Other than that, follow the other poster's suggestions and try to compile and run the program from the terminal.

---

### Post by JC75 on 2012-02-29
Thanks Zugzwang, that worked!

---

