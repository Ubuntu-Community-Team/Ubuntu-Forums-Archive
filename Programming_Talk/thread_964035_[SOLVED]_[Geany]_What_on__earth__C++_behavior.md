---
title: "[SOLVED] [Geany] What on _earth?_ C++ behavior"
date: 2008-10-30
forum: Programming Talk
---

### Post by fiddler616 on 2008-10-30
Hello,
I've just started using Geany to do C++. I made a Hello World program, which looks like this:
```
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])
{
	cout << "Hello World!";
	return 0;
}

```
I then started to make another program with control flow and variables, so I copied everything, so I'd keep the boilerplate, and now, though it compiles, it won't execute, with the error
> Failed to execute the terminal program
It is a *verbatim* copy of the working program--the only difference is that it has a different filename (from test.cpp to guess.cpp)
Any help would be very appreciated. Thanks.

---

### Post by LaRoza on 2008-10-30
Who says IDE's make things easier?

Compile it from the command line. If it works, then it is geany's problem (and not C++).

If you get an error, post the error here.

See the sticky for how to compile from the command line if you don't know how.

---

### Post by mrm48 on 2008-10-30
Geany's functionality has changed from what I remember. For C++, you have to click "Build" in the Build menu (F9), otherwise it will not create a .out file, only pass it through the compiler.

---

### Post by fiddler616 on 2008-10-30
> **LaRoza said:**
> Who says IDE's make things easier?

Compile it from the command line. If it works, then it is geany's problem (and not C++).

If you get an error, post the error here.

See the sticky for how to compile from the command line if you don't know how.
That did it! Kind of weird about Geany, but I have no idea on how to reproduce the problem to consider filing a bug report.

Hrm, +1 Python. Compare
```
python hello.py
```
with
```
g++ hello.cpp -o hello
<ENTER>
./hello
```
Oh well, c'est la vie. I suppose it's healthy.

---

