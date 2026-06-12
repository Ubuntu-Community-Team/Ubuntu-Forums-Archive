---
title: "Python using compiled VTE library"
date: 2009-07-19
forum: Programming Talk
---

### Post by SadaraX on 2009-07-19
EDIT: Problem solved.

I'm working on [VTE]("https://code.launchpad.net/vte"), so I can use it in Python. 

I can compile their source files successfully (using autogen.sh and make), but I do not know how to make a 'vtemodule.so' file that I can actually use in my python programs.

python ./demo-test.py #using the simple demo program they provide in the source files
```

#!/usr/bin/env python
import vte

```

I get the error message:
```

Traceback (most recent call last):
  File "./vte-demo.py", line 6, in <module>
    import vte
ImportError: No module named vte

```

I have no idea what to do. Please help.

My build process so far command line:
```

bzr branch lp:vte
cd vte
./autogen.sh
make
sudo make install
sudo ldconfig
cd python/
python ./vte-demo.py

```

The make and make install process do not seem to produce a vte-module that python sees on my system.

---

### Post by SadaraX on 2009-07-23
Bump with new information about the problem. See first post.

---

