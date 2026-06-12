---
title: "Can't run OpenGL program - X Error of failed request:  BadWindow"
date: 2007-03-08
forum: Programming Talk
---

### Post by smith.norton on 2007-03-08
I have installed the glut development libraries on my Ubuntu 6.06 LTS system. I have installed the following packages:-

```
freeglut3-dev_2.4.0-4_amd64.deb
libgl1-mesa_6.4.1-0ubuntu8_amd64.deb
libgl1-mesa-dev_6.4.1-0ubuntu8_amd64.deb
libgl1-mesa-swrast-dev_6.4.1-0ubuntu8_amd64.deb
libglu1-mesa_6.4.1-0ubuntu8_amd64.deb
libglu1-mesa-dev_6.4.1-0ubuntu8_amd64.deb
mesa-common-dev_6.4.1-0ubuntu8_all.deb
xlibs-dev_7.0.0-0ubuntu45_all.deb
```

Now, I try to compile and run the program I got from here:- [http://nehe.gamedev.net/data/lessons/linux/lesson01.tar.gz](http://nehe.gamedev.net/data/lessons/linux/lesson01.tar.gz)

On executing it, I got the following error.

```
smith@pepsi:~/OpenGL/lesson01$ gcc -lglut lesson1.c
smith@pepsi:~/OpenGL/lesson01$ ./a.out
freeglut (./a.out):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  16
  Current serial number in output stream:  19
```

Please tell me what has gone wrong and how I can correct it and make the code run.

---

### Post by lnostdal on 2007-03-08
try starting glxgears .. does that work?

then paste what glxinfo says

---

### Post by smith.norton on 2007-03-08
[Blank]

Actually this post had a duplicate message, so I removed that.

---

### Post by lnostdal on 2007-03-08
didn't you post this exact same think here: [http://ubuntuforums.org/showthread.php?t=379112](http://ubuntuforums.org/showthread.php?t=379112) ...?

edit:
if you wanted to add information about your graphics-card etc. you could just have edited your post you know

---

### Post by bapoumba on 2007-03-08
@ smith.norton: I've merged your threads.

---

### Post by hod139 on 2007-03-08
Make sure your DRI is set up correctly (try running glxgears as suggested).  Also, I've seen that error message if freeGLUT is not initialized correctly.  Please post more details and code snippets.

---

