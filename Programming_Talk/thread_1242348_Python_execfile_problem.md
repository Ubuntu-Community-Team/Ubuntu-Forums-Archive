---
title: "Python execfile problem"
date: 2009-08-17
forum: Programming Talk
---

### Post by colau on 2009-08-17
Nothing happens if i type python python.py in terminal.
```

import os
filename = os.environ.get('/media/disk/Testing/python.py')
if filename and os.path.isfile(filename):
    execfile(filename)

```
echo $PATH
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by Jacks0n on 2009-08-17
Hm, I don't know why you're using an environmental variable. Environmental variables are traditionally used to make a certain setting known to multiple programs, and they're stored with the shell, not python.

So as far as I understand...

```

print os.environ.get('/media/disk/Testing/python.py')

```

is the same as (in bash)

```

echo "$/media/disk/Testing/python.py"

```

Try this if you want to execute that file in python, from a python script.

```

filename = '/media/disk/Testing/python.py'
try:
    execfile(filename)
except IOError, error:
    print 'Cannot execute file %s. Error: %s' % (filename, error.strerror)

```

---

