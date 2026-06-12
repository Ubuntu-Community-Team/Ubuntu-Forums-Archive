---
title: "When C++ met python..."
date: 2006-12-23
forum: Programming Talk
---

### Post by Wybiral on 2006-12-23
The story of when C++ met python...

```

// pycpp.cpp

#include <Python.h> 
#include <iostream>
 
using namespace std; 
 
int main(){ 
	Py_Initialize(); 

	cout << "\nC++: Hello python, Im C++!" << endl;
	PyRun_SimpleString("print 'Python: Hi C++, Im python! How are you?'\n");
	cout << "C++: Pretty good python, and youself?" << endl;
	PyRun_SimpleString("print 'Python: Fine like wine.'\n");
	cout << "C++: Ok then, Ill C you later :)" << endl;
	PyRun_SimpleString("print 'Python: Not if PY see you first!\\n'\n");

	Py_Finalize(); 
} 

```

Compile that with:
```

g++ pycpp.cpp -I/usr/include/python2.4 -lpython2.4

```

Execute it with:
```

./a.out

```

---

### Post by samjh on 2006-12-24
Hehe... nice one. :)

So where is this python.h?

---

### Post by po0f on 2006-12-24
samjh,

[python-dev](http://packages.ubuntu.com/edgy/python/python-dev)

---

### Post by Wybiral on 2006-12-24
Also, when you compile it, just change the "python2.4" to whatever version of python you have. I just wanted to show how easily python can be integrated into a c++ program. I'm working on some tutorials on the various ways to interface between them, I'll post when I'm done.

[LIST=1]
[*]You can write python modules in C/C++
[*]You can access C++ objects in pythons
[*]You can access python objects in C++
[/LIST]

You can even access the python dictionary to insert variables and stuff, as well as call function's from each other with parameters and returns. Python also offers simple type conversion functions to turn python objects into C int's, floats, and strings.

---

### Post by gh0st on 2006-12-24
It's that age old story. A refined and sophisticated, strongly typed programming language meets a young energetic, dynamically typed language and they fall in love. Their parents don't approve but somehow they overcome the obstacles and everything works out in the end. Roll credits :-)

---

### Post by Game_Ender on 2006-12-24
When python finally learned to get along with C++:
```

#include <boost/python.hpp>
#include <iostream>

using namespace std;
using namespace boost::python;

struct World
{
    void set(std::string msg) { this->msg = msg; }
    std::string greet() { return msg; }
    std::string msg;
};

BOOST_PYTHON_MODULE(hello)
{
    class_<World>("World")
        .def("greet", &World::greet)
        .def("set", &World::set)
    ;
}

/* Now in python:
>>> import hello
>>> planet = hello.World()
>>> planet.set('howdy')
>>> planet.greet()
'howdy'
*/

```

See here for information on using [Boost.Python]("http://www.boost.org/libs/python/doc/tutorial/doc/html/index.html") and just run 'sudo apt-get libboost-python-dev' from the command line to install it.

---

### Post by samjh on 2006-12-25
Game_Ender,

Isn't your use of **std**::string a bit redundant, because of:

using namespace std;

? ;)

---

### Post by po0f on 2006-12-25
samjh,

Nah, it's just *extra*-qualified.  ;)

---

### Post by lloyd mcclendon on 2006-12-25
good stuff


i'd be interested to see a .py file that makes some calls out to some old c++ objects

---

### Post by Wybiral on 2006-12-26
Basically that's how modules for python are written. BTW, the boost library is nice, but I don't think it's really necessary... Python.h offers enough functionality to do most of the thing's you would want... I guess it just depends on the person.


I included the source for viper, which is a python modules that adds variables to the constant script and allows python to call the C++ functions. (It's an OpenGL toolkit for python)

---

### Post by Wybiral on 2006-12-26
When Cpp and python tagged eachother...

Save this as "cppFile.cpp"
```

// Save this as cppFile.cpp

#include <Python.h> 
#include <iostream>
 
using namespace std; 

// Wrap python function into Cpp function...
void pyPrint(char value[]){
	// Grab dictionary from python
	PyObject *pyDict = PyModule_GetDict(PyImport_Import(PyString_FromString("__main__")));
	// Create python tuple for passing Cpp args to python
	// 1 = number of arguments
	PyObject *pArgs = PyTuple_New(1);
	// Set element 0 in tuple to value in form of python string
	PyTuple_SetItem(pArgs, 0, PyString_FromString(value));
	// Call "pyPrint" from python dictionary with pArgs
	PyObject_CallObject(PyDict_GetItemString(pyDict, "pyPrint"), pArgs);
}

// Wrap Cpp function into python...
PyObject *cppPrint(PyObject *self, PyObject *args){ 
	char* value;
	// Grab string ("s") from python arguments
	PyArg_ParseTuple(args, "s", &value);
	// Use value obtained from python function call
	cout << value << endl;
	// Return Py_None (python requires us to return something)
	Py_INCREF(Py_None); 
	return Py_None; 
}

// Create module list for inserting Cpp functions to python
static PyMethodDef pyInsert[] = {
	{"cppPrint", cppPrint, METH_VARARGS, "cppPrint(string)\n"}, 
	// A null object is required at end...
	{NULL, NULL, 0, NULL}
};

int main(){ 
	// Open python file
	FILE* pythonFile = fopen("pyFile.py", "r");
	// Init pythong
	Py_Initialize(); 
	// Add module list functions to python
	Py_InitModule("pyInsert", pyInsert);
	// Tell python to import module list
	PyRun_SimpleString("from pyInsert import *\n");
	// Run python file
	PyRun_SimpleFile(pythonFile, "pyFile.py");
	// Call Cpp-2-python wrapping function
	pyPrint("C++ rulez!!!");
	// End python
	Py_Finalize(); 
} 

```

Save this as "pyFile.py"
```

def pyPrint(value):
	print value

cppPrint("Python rulez!!!")

```

Compile with...
```
g++ cppFile.cpp -I/usr/include/python2.4 -lpython2.4
```

Execute with...
```
./a.out
```

This is an example of cpp calling a python function, and python calling a cpp function (with arguments).

---

