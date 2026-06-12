---
title: "How to solve this error"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by Happykarthi22 on 2012-04-25
hi

I am new to opengl. I downloaded the cube program from videorock tutorials. When i run that i am getting this error. 
```
user@srinivas-VirtualBox:~/Desktop/cube$ make
g++ -Wall -o cube main.cpp imageloader.cpp -lglut -lGLU -lGL
imageloader.cpp: In function ‘Image* loadBMP(const char*)’:
imageloader.cpp:141: warning: suggest parentheses around ‘&&’ within ‘||’
```





Help me resolve this

---

### Post by Mark Phelps on 2012-04-25
Based solely on the error message, it's saying that line 141 of the imageloader.cpp file is coded incorrectly ...

But, you might do better posting this in a Coding section of the forum, not in ABT.

---

### Post by strask on 2012-04-25
That's a warning, not an error... does the rest of the make complete? It might be something you can just ignore.

---

### Post by Happykarthi22 on 2012-04-26
Ok where is the link to coding section. its very difficult to find

---

