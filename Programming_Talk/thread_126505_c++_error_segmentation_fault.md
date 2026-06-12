---
title: "c++ error: segmentation fault"
date: 2006-02-06
forum: Programming Talk
---

### Post by grimdaze on 2006-02-06
ok, i'm running ubuntu 5.10 on a power pc g3 and i'm trying to learn glut. i use this code to create a window:
```
#include <GL/glut.h>

bool init()
{
  return true;
}

void display()
{
}

int main(int argc, char *argv[])
{
  glutInit(&argc,argv);
  glutInitWindowPosition(50,50);
  glutInitWindowSize(640,480);
  glutCreateWindow("My GLUT Window");
  glutDisplayFunc(display);
  if (!init())
    return 1;
  glutMainLoop();
  return 0;
}
```

and this, in a makefile, to complie:
main : main.cpp
	g++ -lGL -lGLU -lglut main.cpp -o main
clean :
	rm -rf main
it all compiles fine but when i try to run the program i get this error:
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Segmentation fault

is this a hardware issue or am i doing something wrong?

---

### Post by Retrix on 2006-02-07
That code works without any problems on my machine, so I would suggest its an issue with your hardware or OpenGL setup. Are you able to run other 3D applications fine?

---

### Post by bartbes on 2006-02-07
As you can obviously see on his error output it is just his computer, actually it's his video card driver. Are you using a special video driver? If so which? And is there a new one?

---

### Post by grimdaze on 2006-02-07
> Are you able to run other 3D applications fine?

none that i've tried. i didn't think a blank window would be an issue.

> Are you using a special video driver? If so which? And is there a new one?
i don't think so. i have an old ATI Rage 128 card. i have no idea what driver it uses. i'm not too knowledgable on the hardware side.

---

