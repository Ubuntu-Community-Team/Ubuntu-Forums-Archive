---
title: "Compiling together multiple files, C++"
date: 2009-09-26
forum: Programming Talk
---

### Post by shynthriir on 2009-09-26
Never mind, ignore this, figured it out.

---

### Post by credobyte on 2009-09-26
```
#include "custom.h"

```In this case, you don't need to do any additional steps - while all the files are in the same directory, g++ will pick them up silently.


Oh, and .. you may want to try:
```
g++ *.cpp -o main
```

---

### Post by nvteighen on 2009-09-26
Well, usually a Makefile is used for this so you don't have to recompile modules that haven't been modified... You just recompile the needed modules and finally relink.

Look at this: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html)

---

