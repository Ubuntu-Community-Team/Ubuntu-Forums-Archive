---
title: "[python] Import Encoded File"
date: 2011-07-18
forum: Programming Talk
---

### Post by Pyro.699 on 2011-07-18
Hello,

What is the best way to import a python file that is encoded in another format (for this example im gonna use base64 since it is very common).

encoded.py
```

def func():
    return "Test"
    
class Class():
    def __str__():
        return "Test"
        
variable = "Test"
print "TesT"

```

encoded.py.b64
```

ZGVmIGZ1bmMoKToKCXJldHVybiAiVGVzdCIKCQpjbGFzcyBDbGFzcygpOgoJZGVmIF9fc3RyX18oKToKCQlyZXR1cm4gIlRlc3QiCgkJCnZhcmlhYmxlID0gIlRlc3QiCnByaW50ICJUZXNUIg==

```

Basically im looking for something that i could type that would essentially be:
```

import imp
encoded = imp.load_source('encoded', './encoded.py')
encoded.func()

```
But it is encoded.

Thanks
~Cody

---

### Post by Bachstelze on 2011-07-18
load_source() wants a real file, not a file-like object, so I think your only choice is to first do the charset conversion, then save the result as a new file and open that with load_source().

---

### Post by Pyro.699 on 2011-07-18
Yeah, i knew that. That's why using it wouldn't work directly.

Im trying to get  *compile* working...
```

import base64
def import_b64(path):
    f = open(path, 'r')
    PythonData = base64.b64decode(f.read())
    exec compile(PythonData, f.name, 'exec')
    f.close()

```

That is as far as i can get at the moment; i dont want it to *exec* though. I need it to act as if a module has been imported.

---

### Post by Bachstelze on 2011-07-19
This seems to work. As I said, you really have to write the decoded data to a new file if you want to load it with load_source

```
import base64
import imp
import os
import tempfile

def import_b64(modname, path):
        ifile = open(path, 'r')
        (ofile, ofilename) = tempfile.mkstemp(suffix='.py')
        data = base64.b64decode(ifile.read())
        os.write(ofile, data)
        os.close(ofile)
        module = imp.load_source(modname, ofilename)
        os.remove(ofilename)
        return module

encoded = import_b64('encoded', 'encoded.py')
print encoded.func()

```

---

