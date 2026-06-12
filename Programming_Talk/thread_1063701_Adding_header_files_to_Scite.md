---
title: "Adding header files to Scite?"
date: 2009-02-08
forum: Programming Talk
---

### Post by ravenum on 2009-02-08
How do I add the path to the header files in Scite? I know that typing the full path in #include would work, but I also edit my program on other PCs so having that to change everytime would be a major PITA. Any suggestions?

---

### Post by nvteighen on 2009-02-08
#include "someheader.h" uses relative paths.

So, if you type #include "hello.h", it will look at the same directory the source code is.

And #include <someheader.h> looks at the places the compiler is told to (using the -I flag or the default system place), so there's no issue with it.

---

