---
title: "Python Using C Modules"
date: 2008-10-21
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-10-21
I've googled a bit, and found quite a few tutorials on writing C modules to use in Python code. However, I don't find any of these tutorials to be straight-forward enough for my purposes. For now, I just want the basics. Just for practice, I want to write a C module containing a function to print "hello" on the screen, and call it using Python.

Can someone give a simple example of how this is done?

---

### Post by pmasiar on 2008-10-21
Wybiral is not around for quite a while - hopefully he has more productive way to spend his time :-) Try to PM him. I believe he did it.

---

### Post by Rich78 on 2008-10-21
This looks like it could cover what you're looking for.

[http://www.python.org/doc/2.5.2/ext/simpleExample.html]("http://www.python.org/doc/2.5.2/ext/simpleExample.html")

You could pass any system command through it from Python.

Python:
```

>>> import spam
>>> status = spam.system("echo hello world")

```

C:
```

#include <Python.h>
static PyObject *
spam_system(PyObject *self, PyObject *args)
{
    const char *command;
    int sts;

    if (!PyArg_ParseTuple(args, "s", &command))
        return NULL;
    sts = system(command);
    return Py_BuildValue("i", sts);
}

```

---

### Post by snova on 2008-10-21
This is what I figured out from five minutes in the API docs:

helloutils.c:

[PHP]
#include <Python.h>

static PyObject* helloutils_output( PyObject* self, PyObject* args )
{
    printf( "Hello!\n" );
    Py_RETURN_NONE;
}

static PyMethodDef HelloutilsMethods[] =
{
    { "output", helloutils_output, METH_VARARGS, "Prints \"Hello!\\n\"." },
    { NULL, NULL, 0, NULL }
};

PyMODINIT_FUNC inithelloutils()
{
    PyObject* module = Py_InitModule( "helloutils", HelloutilsMethods );
}
[/PHP]

Compile:

```
gcc -fPIC helloutils.c -o helloutils.so -I/usr/include/python2.5 -shared
```

Example:

[PHP]
>>> import helloutils
>>> helloutils.output()
Hello!
>>>
[/PHP]

The C code was mostly copied from the documentation.

---

