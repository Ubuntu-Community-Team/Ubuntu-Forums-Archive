---
title: "Dynamic python code execution module..."
date: 2006-12-13
forum: Programming Talk
---

### Post by Wybiral on 2006-12-13
This is a little piece of code that allows you to dynamically execute python code in your python scripts. I'm not sure if something like this already exists, I just thought it would be interesting to have if it didn't. Here is the C++ code...

```

#include <Python.h> 
 
using namespace std; 
 
PyObject *pyCode(PyObject *self, PyObject *args){ 
	const char *pyCode;
	PyArg_ParseTuple(args, "s", &pyCode);
	PyRun_SimpleString(pyCode);
	Py_INCREF(Py_None); 
	return Py_None; 
} 
 
// Register function for use in python // 
static PyMethodDef pyCodeMod[] = { 
   {"pyCode", pyCode, METH_VARARGS, "pyCode(string)\n"}, 
   {NULL, NULL, 0, NULL}
}; 
 
int main(){ 

  // Open python script to execute
	char pySrc[]="test.py";
	FILE* pyFile = fopen(pySrc, "r");

	Py_Initialize(); 

	// Import C++ module in python
	Py_InitModule("pyCodeMod", pyCodeMod);
	PyRun_SimpleString("from pyCodeMod import *\n");

	// Execute python script
	PyRun_SimpleFile(pyFile, pySrc);

	Py_Finalize(); 
} 

```

Now, compile that with...
```
g++ pyCodetest.cpp -I/usr/include/python2.5 -lpython2.5
```
Assuming that you saved the source in "pyCodetest.cpp" and that you have python 2.5 installed (change those values to fit your setup).

Then you can create a python script called "test.py" that uses the pyCode function, something like this will work...

```

pyCode("print 'Dynamic python code execution!'")

```

Then, when you execute the file produced by compiling the CPP code, the file "test.py" will be executed and the pyCode function will be usable. This can also be turned into a real python module so that you don't have to execute it through a cpp executable.

Anyway, just thought I would share this... There is a lot you can do with dynamically generated code, your programs can generate and execute programs!

---

### Post by pmasiar on 2006-12-13
I am not sure if I understand: can you get any text file with a valid python code, and execute it from inside of a C++ program? So you can use C++ as scripting language to glue pieces of python together? And get result values somehow? 

Not sure why C++ is better than using bash or python as glue language. What I am missing?

---

### Post by Wybiral on 2006-12-13
BTW, if you did want to make a module from something like this so that a C++ executable isn't required, its pretty simple. Create this C file...

```

// Save this as pyCode.c

// Compile to object using something like this:
// gcc -c pyCode.c -I/usr/include/python2.4 -I/usr/lib/python2.4

// Create shared object using this:
// ld -shared -o pyCode.so pyCode.o -lpython2.4

// Then you should have the file "pyCode.so" and that all you need!

#include <Python.h> 
 
PyObject *pyCode(PyObject *self, PyObject *args){ 
	const char *pCode;
	PyArg_ParseTuple(args, "s", &pCode);
	PyRun_SimpleString(pCode);
	Py_INCREF(Py_None); 
	return Py_None; 
} 
 
static PyMethodDef pyCodeMod[] = {
   {"pyCode", pyCode, METH_VARARGS, "pyCode(string)\n"}, 
   {NULL, NULL, 0, NULL}
};
 

PyMODINIT_FUNC initpyCode(void) {
	(void) Py_InitModule("pyCode", pyCodeMod);
}

```

I wrote the instructions on the top of that source, follow those and you will create a file called "pyCode.so" which is the shared object file that links your module to python. Then you can import it into your python project like this...

```

from pyCode import *

pyCode("print 'Hello, I am dynamically executed code!'")


```

And there you have it, your own module that allows for dynamic code creation!


Here it is for anyone who doesn't want to mess with compiling it: [http://p13.wikispaces.com/space/showimage/pyCode.so](http://p13.wikispaces.com/space/showimage/pyCode.so)

Just put that in your project folder and remember to import it using "from pyCode import *"

Then you use it with the command "pyCode('Python code goes here')"

EDIT: You can use python as a scripting language for C and C++, and you can do A LOT with it. This example is just to create a new module for python, but you can also use embedded python to communicate both ways between C++ and python... VERY powerful stuff!

---

### Post by Jengu on 2006-12-13
This is very very very unnecessary ;p

You can already accomplish this in python code by doing:

```

exec("print 'Hello, I am dynamically executed code!'")

```

It's a builtin function :) The reason it's so unnecessary though is because there's never ever ever any reason to do it. I do not know of a single good reason to use exec that shouldn't be replaced by something else. It's also insecure to pass any input to, since it potentially lets users make your program run arbitrary code. Good learning the Python C API though :)

---

### Post by Wybiral on 2006-12-13
Wow, cool. Like I said, I didn't know if one already existed. But, at least this post is worth the info on creating modules.

It can actually be useful for things like complicated genetic algorithms, you can have the "dna" sequence of the organism generate it's own code instead of having to create large systems of parsing the "dna".

Other than that... User submitted code, say you want your users to be able to create an object and call it from within the program.. This is a simple way to allow that.

Thanks for the info, maybe I'll write a tutorial on create a module that doesn't already exist... lol

---

### Post by engla on 2006-12-14
> **Jengu said:**
> This is very very very unnecessary ;p

You can already accomplish this in python code by doing:

```

exec("print 'Hello, I am dynamically executed code!'")

```

It's a builtin function :) The reason it's so unnecessary though is because there's never ever ever any reason to do it. I do not know of a single good reason to use exec that shouldn't be replaced by something else. It's also insecure to pass any input to, since it potentially lets users make your program run arbitrary code. Good learning the Python C API though :)

Nope. Say for example you have an application you have written in C++, and you want to add python scripting capabilities.. Now you can enable your **users** to use the easy language python to customize or interact with your app, and you don't have to port the app to python -- you can continue to develop it in C++ (because you like that best/works best with qt or whatever)

---

### Post by &lt;mawe&gt; on 2006-12-14
Wouldn't this be a nice entry for the [Python Cookbook](http://aspn.activestate.com/ASPN/Cookbook/Python)?

---

