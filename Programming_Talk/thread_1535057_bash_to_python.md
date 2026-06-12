---
title: "bash to python"
date: 2010-07-20
forum: Programming Talk
---

### Post by P.ap G on 2010-07-20
Any suggestions on re-writing this function I wrote into python , I'm getting stuck giving `raw_input`
multiple arguments?

---

### Post by Can+~ on 2010-07-20
Easy path:

[PHP]filename = raw_input("Name of the file:")
permissions = raw_input("Octal Permissions:")[/PHP]

The other way, would be to split, working on all this different inputs:

```
"Name of the file.txt" 775
Name\ of\ the\ file.txt 775
Nameofthefile.txt 775
```

But, you can also exploit the command-line arguments, as bash already splits it accordingly, saving you time. For example, I made this little program:

[PHP]#!/usr/bin/env python

import sys

print sys.argv[/PHP]

Testing it:

```
:~/Desktop$ python asdf.py "Filename with spaces.txt" 777
['asdf.py', 'Filename with spaces.txt', '777']
:~/Desktop$ python asdf.py Filename\ with\ spaces.txt 777
['asdf.py', 'Filename with spaces.txt', '777']
:~/Desktop$ python asdf.py filenamewithoutspaces.txt 777
['asdf.py', 'filenamewithoutspaces.txt', '777']

```

Are you rewriting this in python for any particular reason? Learning? Cross-compatibility?

---

