---
title: "How can I check to see if a file exisits ? in python"
date: 2007-12-09
forum: Programming Talk
---

### Post by thenetduck on 2007-12-09
Hi

I am writing a little program and am at the point where I would like to determine if a "backup" directory has been created or not. If it has, it will do it's normal thing but if it hasn't it will create a new one etc. I know about an IOError try except, but is there a better way to do it with one if statement? For instance is there an IO function that will return a bool? 

Thanks

The Net Duck

---

### Post by thenetduck on 2007-12-09
nm found the import os thing....

BTW: I tried to use os.access(path,mode) but when I put in F_OK for my mode ,it tell's me it doesn't exist. It only works if i put an int in place of the mode. I don't get it. 

The Net Duck

---

### Post by adelgado on 2007-12-09
You could use
```

import os

# ...

if os.access(Filename, os.F_OK):
    #Do something
else:
    #Do some other thing.


```

More info at [http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)

---

### Post by adelgado on 2007-12-09
> **thenetduck said:**
> nm found the import os thing....

BTW: I tried to use os.access(path,mode) but when I put in F_OK for my mode ,it tell's me it doesn't exist. It only works if i put an int in place of the mode. I don't get it. 

The Net Duck

Posted while I was writing. You used "F_OK" or "os.F_OK"?

---

### Post by geirha on 2007-12-09
you can also use ```
if os.path.isfile(path): print "yay"
```

---

### Post by engla on 2007-12-09
Or ```
os.path.exists(file_path)
```

---

### Post by thenetduck on 2007-12-09
> **adelgado said:**
> Posted while I was writing. You used "F_OK" or "os.F_OK"?

F_OK but I like the bottom two they seem simpler, unless their is any reason not to use them. 

The Net Duck

---

### Post by geirha on 2007-12-10
Looking a bit closer I see that os.path.isfile is wrong since it's a directory you're checking, so os.path.isdir would be the function you should use. It doesn't matter which of os.access, os.path.exists or os.path.isdir you choose, but obviously they don't do the exact same thing.

os.path.exists(path) does the same as os.access(path, os.F_OK), simply checking if that path exists. It does not determine whether it is a file or directory however. That's what os.path.isdir and os.path.isfile does.

In your case it's probably best to use both os.path.isdir(path) to determine it is a dir, and os.access(path, os.W_OK) to check that you also have write access to the directory.

EDIT: also, you can cut away the "os."-part by importing with
```
from os import *
if path.isdir(backup_dir) and access(backup_dir, W_OK):
  ...

```

---

### Post by Majorix on 2007-12-10
I would suggest reading this:
[http://docs.python.org/lib/module-os.path.html](http://docs.python.org/lib/module-os.path.html)

---

