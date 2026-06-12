---
title: "Importing c++ into python"
date: 2009-04-10
forum: Programming Talk
---

### Post by dodle on 2009-04-10
Can I run a C++ program from within the python interpreter or a program?

I want to run the simple C++ *Hello World* program, that prints "Hello World" to the command line, from python.

testc.cpp
[PHP]#include <iostream>
using namespace std;

int main()
{
    cout << "Hello World\n";
    return 0;
}[/PHP]
How would I import and run the compiled testc?

**Edit:** Or am I supposed to get the c++ functions from the source?

---

### Post by pmasiar on 2009-04-11
In Python, you can execute any external program

---

### Post by WW on 2009-04-11
Check out the [subprocess](http://docs.python.org/library/subprocess.html) module.  The simplest version is probably the call() function.  Here's a quick demonstration:
```

$ ls
hello.cpp
$ g++ hello.cpp -o hello
$ ./hello
Hello World
$ python
EPD_Py25 (4.2.30201_beta1) -- http://www.enthought.com

Python 2.5.4 |EPD_Py25 4.2.30201_beta1| (r254:67916, Mar 27 2009, 01:52:11) 
[GCC 4.0.1 (Apple Computer, Inc. build 5370)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from subprocess import call
>>> status = call("./hello")
Hello World
>>> status
0
>>> 

```

---

### Post by happysmileman on 2009-04-11
As posted above you can just call("./programname") to do it.

If you want to actually be able to INTERFACE with C++ code, you can code Python Modules in C/C++ and import them just as you would any other python module.

Brief description can be found [here](http://www.python.org/doc/ext/intro.html). Even if all you need right now is to call("./programname") it might be good to remember that it's possible to do this for the future, if you need to incorporate C/C++ into a Python program.

---

### Post by nvteighen on 2009-04-12
> **happysmileman said:**
> 
If you want to actually be able to INTERFACE with C++ code, you can code Python Modules in C/C++ and import them just as you would any other python module.


Hmm... At least for C libraries (which would be the equivalent for "modules"), you have to use the ctypes module in order to be able to interface Python with C data types. Look at: [http://docs.python.org/library/ctypes.html](http://docs.python.org/library/ctypes.html)

No idea about C++, but it should be similar, I guess.

---

