---
title: "C++ and OpenGl error"
date: 2008-01-29
forum: Packaging and Compiling Programs
---

### Post by JMar13 on 2008-01-29
Ok, i was reading threads trying to figure out a simple way to get opengl to work with gedit.  I tried to add packages and what not that were recommended, but when trying to execute my:

"g++ program.cpp -glut"  

i recieve this: 

"cc1plus: error: unrecognised debug output level "lut"" 

 ive tried numerous simple C++/OpenGL programs and they all give me the same error.  

any help would be greatly appreciated

---

### Post by Zugzwang on 2008-01-30
> **JMar13 said:**
> O
"g++ program.cpp -glut"  


The correct command would be:
```

"g++ program.cpp -lglut"

```

The -g command line switch is about debugging symbols in the executable, -l is for including libraries.

---

