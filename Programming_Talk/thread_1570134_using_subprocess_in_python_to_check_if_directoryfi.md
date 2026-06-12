---
title: "using subprocess in python to check if directory/file exists"
date: 2010-09-07
forum: Programming Talk
---

### Post by linuxonbute on 2010-09-07
i am trying to write some python code and one part is to set up some directories and files. This part of the program should see if a directory exists and if not then create it. The os.system etc allows me to do that but is deprecated so I want to use subprocess but cannot find the syntax for the various options.

using standard linux command line I could do something like:
```

#!/bin/bash
if [ -d $HOME/1-wire ] 
then
    echo .
else
	mkdir $HOME/1-wire
fi

```
I would like do do something on these lines with python's subprocess module but can find no examples to do this.
Any help would be appreciated.
thanks

---

### Post by StephenF on 2010-09-07
And your first instinct is to go with what you know and jump to a shell. :rolleyes:

```

import os

pathname = os.path.join(os.path.expanduser('~'), '1_wire')

try:
    os.mkdir(pathname)
except OSError, e:
    if e.errno == 17 and os.path.isdir(pathname):
        print '.'
    else:
        raise

```

---

### Post by linuxonbute on 2010-09-11
> **StephenF said:**
> And your first instinct is to go with what you know and jump to a shell. :rolleyes:
Err no as I said I want to do in python what that shell stuff does.
> 
```

import os

pathname = os.path.join(os.path.expanduser('~'), '1_wire')

try:
    os.mkdir(pathname)
except OSError, e:
    if e.errno == 17 and os.path.isdir(pathname):
        print '.'
    else:
        raise

```

I could do to find out where I can find the syntax for this.
How did you find out?

---

### Post by Bachstelze on 2010-09-11
The idea is that you don't really need to check beforehand whether the directory exists. You try to create it, and if it fails, you find out why.

---

### Post by linuxonbute on 2010-09-11
So could I simply do 

```


pathname = os.path.join(os.path.expanduser('~'), '1_wire')

if os.path.isdir(pathname):
      print '.'
else:
      os.mkdir(pathname)


```

Forget this i can see it could work but doesn't handle errors and I guess that at my level of knowledge

try, try finally and except could be especially useful.

---

### Post by Bachstelze on 2010-09-11
> **linuxonbute said:**
> So could I simply do 

```


pathname = os.path.join(os.path.expanduser('~'), '1_wire')

if os.path.isdir(pathname):
      print '.'
else:
      os.mkdir(pathname)


```

It's a bad idea, because there are other reasons why the mkdir could fail (maybe Python doesn't have permission to do it). In that case, you would end up with an uncaught exception.

---

