---
title: "[Python] os.stat('file')"
date: 2008-08-05
forum: Programming Talk
---

### Post by TreeFinger on 2008-08-05
Well I don't know who is familiar with os.stat() but I am wondering how you get the information to print into readable form.

os.stat() just spits a tuple out with numbers. I know what information this regards (last access time, etc) but how do I get that printed in a readable form?
```

>>> os.stat('.')
(16895, 0L, 0, 0, 0, 0, 0L, 1217961252, 1217427367, 1216048629)

```

---

### Post by era86 on 2008-08-05
Why not go through the tuple and print it out from there?  Do like..

my_stat = os.stat()

Or something and travrse the tuple printing out info as you go.

Does that answer your question?  Maybe I misunderstood.  Let me know.

---

### Post by TreeFinger on 2008-08-05
> **era86 said:**
> Why not go through the tuple and print it out from there?  Do like..

my_stat = os.stat()

Or something and travrse the tuple printing out info as you go.

Does that answer your question?  Maybe I misunderstood.  Let me know.

That would just print out that number that has no meaning to a human.

I believe the way to go about it is:
```

import os, time, os.path, stat
stats = os.stat('file name')
print time.strftime("%m/%d%Y",time.localtime(stats[stat.ST_ATIME]))

```

If there is a better way, please inform me!

---

### Post by geirha on 2008-08-05
More or less. os.stat returns an instance of stat_result though, which means you don't need to import the stat module. help('os.stat_result')
```
import os, time
print time.strftime("%Y-%m-%d", time.localtime(os.stat('file name').st_atime))
print time.ctime(os.stat('file name').st_mtime)

```

---

### Post by era86 on 2008-08-05
Double post...

---

### Post by samjh on 2008-08-05
> **TreeFinger said:**
> I believe the way to go about it is:
```

import os, time, os.path, stat
stats = os.stat('file name')
print time.strftime("%m/%d%Y",time.localtime(stats[stat.ST_ATIME]))

```

If there is a better way, please inform me!

Sometimes, you do need to do some manual work to get what you want. ;)

If you haven't already done so, read the entry for stat() here:
[http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)

And also examine the symbolic indexes here:
[http://docs.python.org/lib/module-stat.html](http://docs.python.org/lib/module-stat.html)

Example for file size:
```
import os

thestat = os.stat("myfile")
print "size =", thestat[6], "bytes"
```

---

### Post by bvmou on 2008-08-06
The simplest thing is to call 
```
os.stat('/the/file.ext').st_size 

```or 
```
os.stat('the_item').st_mtime 
```
and then do some arithmetic on the output, like dividing the .st_size call by 1000 and giving a human friendly value in megabytes, or putting the mtime call in an 'hours ago' format along the lines geirha suggests.

---

