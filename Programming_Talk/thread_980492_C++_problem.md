---
title: "C++ problem"
date: 2008-11-12
forum: Programming Talk
---

### Post by phantomgunex on 2008-11-12
I just programmed a simple program to cout "hi" in terminal using geany:
```
#include <iostream>
#include <stdlib.h>

using namespace std;

int main(int argc, char** argv)
{
	cout << "hi" << endl;
	return 0;
}
```

but i get the output: "hi there"
i once made a program to cout "hi there" a few days ago and since then every program i wrote gave me that same output. help me please!!!](*,)

---

### Post by Shwefty on 2008-11-12
Hmmm, sounds to me like there's something up when compiling.  Apparently the last thing that compiled correctly was the "hi there" program. So, whenever you execute, the last correctly compiled program spews out.

---

### Post by phantomgunex on 2008-11-12
forgive me i just started learning programming C++. So what do i do???

---

### Post by jimi_hendrix on 2008-11-12
try ```
g++ -o executablename filename.cpp
``` where executablename is what ever you want and filename is the name of the main file

---

### Post by Shwefty on 2008-11-12
Haha, don't worry, I've *never* programmed in c++.  I have in C though.  You have to compile your program after you write it, *then* you can execute it.  The compiler for C++ is called g++.

[Helpful link]("http://www.linuxquestions.org/questions/programming-9/compiling-c-in-linux-107419/")

[Possibly even more helpful]("http://forums.devshed.com/c-programming-42/how-to-run-c-program-from-linux-47357.html")

In short, the code should look something like:

```
g++ **Your_Program_Name.C**
```

Then after it compiles:

```
./a.out
```

---

### Post by phantomgunex on 2008-11-12
thats weird when i try to build it... the output i get the output i want...

---

### Post by snova on 2008-11-12
What exactly are you doing? List *all* the steps you are taking.

---

### Post by jimi_hendrix on 2008-11-12
> **phantomgunex said:**
> thats weird when i try to build it... the output i get the output i want...

you want the output you want dont you?

---

