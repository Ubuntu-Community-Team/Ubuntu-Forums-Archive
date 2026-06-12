---
title: "[Python]How do I import files from other directory"
date: 2009-05-04
forum: Programming Talk
---

### Post by Mister LinOx on 2009-05-04
Okay. I have been experimenting with python by creating some programs/scripts and then saving them to my documents/Python Files(created folder). The thing is, I have no idea how to import something OUT of the default python directory.

  It was easier in XP, as the default save location was where the other modules were at. In Ubuntu, I can't seem to find this directory or where I should save the files to or how to import them. Help?

---

### Post by days_of_ruin on 2009-05-04
```
import sys
sys.path.append('path/to/your/module')
import mymodule
```

---

### Post by DocForbin on 2009-05-04
Or use distutils to install your module. It's gravy.

python myscript.py install

[http://docs.python.org/install/index.html](http://docs.python.org/install/index.html)

---

### Post by regomodo on 2009-05-04
#

---

### Post by Mister LinOx on 2009-05-05
Ah, I see now. Thank you, guys.
I ended up using the:```
sys.path.append
``` way.

---

### Post by ntanitime on 2012-03-02
Thanks you, I've the same problem ;)

---

### Post by Tony Flury on 2012-03-02
Does import not follow symbolic links ? if so that might be an option.

---

