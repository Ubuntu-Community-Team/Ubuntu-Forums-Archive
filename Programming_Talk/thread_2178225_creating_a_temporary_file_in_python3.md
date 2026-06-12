---
title: "creating a temporary file in python3"
date: 2013-10-02
forum: Programming Talk
---

### Post by wingnut2626 on 2013-10-02
```
import tempfile
a = tempfile.TemporaryFile(prefix='myfile',suffix='tmp')

>>> a.write('hello temp world')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' does not support the buffer interface
```

what do i need to do so that i can write to the tempfile?  The documentation says that the default mode is sufficient......

---

### Post by spjackson on 2013-10-02
This is to do with Unicode strings versus bytes strings. You need
```

a.write(b'hello temp world')

```

---

### Post by MadCow108 on 2013-10-03
its better to be explicit about the encoding:
```
a.write('hello temp world'.encode("UTF-8"))
```
just casting to bytes will fail if the string does not only contain ascii (which it can in python3).

---

