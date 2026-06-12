---
title: "Freeglut and Qt creator"
date: 2013-08-31
forum: Packaging and Compiling Programs
---

### Post by Vormeph on 2013-08-31
I am trying to compile an openGL program using freeglut which I installed on my Ubuntu installation. When I try to compile my program under Qt creator, I get the following errors:

```


error: undefined reference to 'glClearColor'
error: undefined reference to 'glClear'
error: undefined reference to 'glColor3f'

...etc

```

How do I solve this issue? Please provide instructions!

---

### Post by zheng1733 on 2013-09-07
Did you include "QT += opengl" in your XX.pro file?

---

