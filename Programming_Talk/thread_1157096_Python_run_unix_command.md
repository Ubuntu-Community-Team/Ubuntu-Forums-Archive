---
title: "Python run unix command"
date: 2009-05-12
forum: Programming Talk
---

### Post by prem1er on 2009-05-12
I'm trying to call a unix command from my python code.  The docs I have read say to call os.mkdir.  This doesn't seem to working for me to create a directory.  I get the error "file does not exist /foo/bar/".  What am I doing wrong.  Thanks.

```

import os

if os.path.exists(path):
   print 'Path exists'
else:
   os.mkdir(path)
```

---

### Post by dandaman0061 on 2009-05-12
does the parent directory '/foo' exist?

If not you need to create this one first OR use 'os.makedirs(path)' which creates directories recursively.

---

### Post by prem1er on 2009-05-12
O yea.  I'm not looking at the machine right now, but that seems like exactly what the problem is.  Thank you.

---

