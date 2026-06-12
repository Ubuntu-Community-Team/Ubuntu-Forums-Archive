---
title: "Python - Search for and create directory"
date: 2006-11-18
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-18
Hey all


Can Python search along a path (given to it via a string) and see if a directory is there. If it can, can I then create a directory?

Any answers would be really helpful

Thanks

Ironfistchamp

---

### Post by po0f on 2006-11-18
ironfistchamp,

Try os.walk() or os.path.walk(), one of those is bound to be what you are looking for.

---

### Post by ironfistchamp on 2006-11-19
Thank you I shall look them up.

---

### Post by xtacocorex on 2006-11-19
In my Autokernel code, we check to see if /tmp/autokernel is there and if not, we create it. Here is the code for that:
```

# Create '/tmp/autokernel' if it does not exist. 
if not os.access('/tmp/autokernel', os.F_OK):
    os.mkdir('/tmp/autokernel')

```
Hopefully this helps some also.

---

### Post by dwblas on 2006-11-20
Similiar to above:
```
import os
def Check_Create_Dir( full_path_name ) :
     if not os.path.isdir(full_path_name)
          os.mkdir( full_path_name )
```

---

