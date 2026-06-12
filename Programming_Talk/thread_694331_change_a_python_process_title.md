---
title: "change a python process title"
date: 2008-02-11
forum: Programming Talk
---

### Post by RawMustard on 2008-02-11
Is there no way to change the title of a python process?
I mean if I have 3 different python scripts running, they're all called python.

This makes it hard to kill ?which python????

Sorry if this is a dumb question, I'm not a seasoned programmer :(

---

### Post by ghostdog74 on 2008-02-11
one way, you can use os.getpid() from inside your Python script. 
```

#!/usr/bin/python
import os
open("file","w").write(os.getpid()) 
#...remaining code

```

then from the command line, whenever you want to kill it
```

# kill $(cat file)

```

---

### Post by RawMustard on 2008-02-12
Thanks.  I know about that, but not what I was looking for.

---

### Post by PaulFr on 2008-02-13
Does the following work for you ? It requires PyInline available at **[http://pyinline.sourceforge.net/](http://pyinline.sourceforge.net/)**```
#!/usr/bin/env python

import dl
import PyInline
import time

libc = dl.open('/lib/libc.so.6')
if libc != 0 : libc.call('prctl', 15, 'fakename\0', 0, 0, 0)
else : print ('prctl not called')

m = PyInline.build(code=r"""
    #include <Python.h>
    #include <stdio.h>
    #include <string.h>

    void set_argv(char *str){
        int argc;
        char **argv;
        Py_GetArgcArgv(&argc, &argv);
        strncpy(argv[0], str , strlen(str));
        memset(&argv[0][strlen(str)], '\0', strlen(&argv[0][strlen(str)]));
    }
    """, language="C")

m.set_argv('fakename')
while 1 :
    print ('ha ha ha ')
    time.sleep (1)
```1. The prctl call is for killall and top on Linux.
2. The m.set_argv call is for ps.

---

### Post by x0x on 2008-12-11
[http://code.google.com/p/procname/](http://code.google.com/p/procname/)

---

