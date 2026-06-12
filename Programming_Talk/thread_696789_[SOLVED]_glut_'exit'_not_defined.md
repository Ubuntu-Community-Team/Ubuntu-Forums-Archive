---
title: "[SOLVED] glut 'exit' not defined"
date: 2008-02-14
forum: Programming Talk
---

### Post by destructchaos on 2008-02-14
i'm taking a computer graphics course this semester and i've got everything set up to compile c++ w/ glut in kdev, but when i try to compile some simple example code from class, i get an interesting error that doesn't show up when i compile on windows:

```

/home/rick/graphics/test_1/src/test_1.cpp: In function ‘void keyboard(unsigned char, int, int)’:
/home/rick/graphics/test_1/src/test_1.cpp:81: error: ‘exit’ was not declared in this scope

```

my teacher is a mac guy and won't help me with linux, so any help is greatly appreciated.

---

### Post by stroyan on 2008-02-14
This message isn't really related to glut.
You need a header file that declares the exit() function.
```
#include <stdlib.h>
```

---

