---
title: "Embedding Python in C++"
date: 2009-03-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-22
So how can I do this:
[list]
[*]Load 5 Python scripts
[*]Pre-compile the scripts for fast executing
[*]Run each script many times in isolated environments
[/list]
I have read some tutorials about but no idea how to do it.

---

### Post by slavik on 2009-03-22
This should explain everything: [http://www.python.org/doc/2.5.2/ext/embedding.html](http://www.python.org/doc/2.5.2/ext/embedding.html)

---

### Post by crazyfuturamanoob on 2009-03-22
How can I import Python modules from sub-folders? 

Python gives ImportError when I try to load the scripts.

```

PyObject *filename, *py_script, *function;

filename = PyString_FromString( "data/python/script.py" );

py_script = PyImport_Import( filename );

Py_DECREF( filename );

if ( py_script == NULL )
{
    PyErr_Print();
}
else
{
    function = PyObject_GetAttrString( py_script, "hello" );
}

```

Edit: Got working with this after Py_Initialize():
```

PyRun_SimpleString( "from sys import path\nfrom os import getcwd\npath.append( getcwd() + \"/data/python\" )\n" );

```
Without ugly \n's:
```

from sys import path
from os import getcwd
path.append( getcwd() + "/data/python" )

```

---

