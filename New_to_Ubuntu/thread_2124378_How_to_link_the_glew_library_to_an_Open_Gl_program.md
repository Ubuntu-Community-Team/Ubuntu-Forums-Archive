---
title: "How to link the glew library to an Open Gl program"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by farrington on 2013-03-10
This is what I type on the terminal:
g++ -o a glm.o Test-Load-ObjFile.o -lGlEW -lglut -lGL -lGLU

This is the error I get:
/usr/bin/ld: cannot find -lGlEW
collect2: ld returned 1 exit status

My distrubutuion is Ubuntu 12.04 x86_64

How can I solve this?

---

### Post by Impavidus on 2013-03-10
I imagine it's case sensitive. Try **-lGLEW**.

---

