---
title: "opengl oop"
date: 2010-08-20
forum: Programming Talk
---

### Post by Adrian Nania on 2010-08-20
Hello all,

I tried to wrap this simple opengl code into C++:
```
/// file = main.cpp
#include "../gltools.h"

void RenderScene(void)
{   glClear(GL_COLOR_BUFFER_BIT);
    glFlush();
}
void SetupRC(void)
{   glClearColor(0.25f, 0.25f, 0.2500001f, 1.0f);
}
void normalKeys(unsigned char key, int x, int y)
{   if (key == 27) //Esc key pressed => exit
    exit(0);
}
int main(int argc, char **argv)
{   glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGBA);
    glutCreateWindow("Simple");
    glutFullScreen();
    glutKeyboardFunc(normalKeys);
    glutDisplayFunc(RenderScene);
    SetupRC();
    glutMainLoop();
    return 0;
}
```
since I do not have the skills for this task, I followed this tutorial: [http://paulsolt.com/2009/07/openglglut-classes-oop-and-problems]("http://paulsolt.com/2009/07/openglglut-classes-oop-and-problems"). Do not forget to check the link Paul was kind to provid for free with a fully working examle.
I tried something like this:
```
/// file = main.cpp
#include "AnimationFramework.h"
int main(int argc, char *argv[])
{   AnimationFramework *f = new AnimationFramework();
    f->setInstance(f);
    f->startFramework(argc, argv);
    return 0;
}
```
```
///AnimationFramework.h
#include "../gltools.h"  ///OpenGL toolkit, system dependent setting, and special general functions
class AnimationFramework
{
protected:
    static AnimationFramework *instance;
public:
    static void setInstance(AnimationFramework * framework);
	static void renderSceneWrap(void);
	static void normalKeysWrap(unsigned char key, int x, int y);
    void startFramework(int argc, char *argv[]);
    virtual void renderScene(void);
    virtual void normalKeys(unsigned char key, int x, int y);
    virtual void setupRC();
};
void AnimationFramework::startFramework(int argc, char *argv[])
{   ///initialize GLUT
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGBA);
    glutCreateWindow("Simple");
    glutFullScreen();
    ///function callbacks
    glutKeyboardFunc(normalKeysWrap);
    glutDisplayFunc(renderSceneWrap);
    setupRC();
    ///start main
    glutMainLoop();
}
///virtual instance functions
void AnimationFramework::renderScene(void)
{   glClear(GL_COLOR_BUFFER_BIT);
    glFlush();
}
void AnimationFramework::setupRC(void)
{   glClearColor(0.25f, 0.25f, 0.2500001f, 1.0f);
}
void AnimationFramework::normalKeys(unsigned char key, int x, int y)
{   if (key == 27)
        exit(0);
}
///call from static callback functions
void AnimationFramework::renderSceneWrap(void)
{   instance->renderScene();
}
void AnimationFramework::normalKeysWrap(unsigned char key, int x, int y)
{   instance->normalKeys(key, x, y);
}
void AnimationFramework::setInstance(AnimationFramework * framework)
{	instance=framework;
}
AnimationFramework *AnimationFramework::instance = 0;

```
Adi

---

### Post by Sockerdrickan on 2010-08-20
Learn C++ **FIRST**

---

### Post by Adrian Nania on 2010-08-20
I managed to fix the code and I hope other people interested could save some time. While this working example is not for experienced programmers, for beginners like me could prove useful.

---

### Post by Adrian Nania on 2010-08-22
Many thanks to Sockerdrickan for his friendly help. I wonder if he got all his 1992 beans with his template response.
All the best

---

### Post by Sockerdrickan on 2010-08-22
> **Adrian Nania said:**
> Many thanks to Sockerdrickan for his friendly help. I wonder if he got all his 1992 beans with his template response.
All the best
I got them while wanking to threads that ask users for help with homework.

---

### Post by Adrian Nania on 2010-08-22
I am as far as you can get from programming. At home and on my personal time only I am playing with some programming examples. Next time maybe you can just ignore questions, don't assume you know who is asking for help.
All the best

---

