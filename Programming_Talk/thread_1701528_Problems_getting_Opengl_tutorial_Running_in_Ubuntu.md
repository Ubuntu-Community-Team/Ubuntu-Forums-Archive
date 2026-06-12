---
title: "Problems getting Opengl tutorial Running in Ubuntu"
date: 2011-03-06
forum: Programming Talk
---

### Post by Jonas thomas on 2011-03-06
I wanted to see if I could set up a code::blocks project file to run this opengl tutorial[URL="http://www.videotutorialsrock.com/opengl_tutorial/crab_pong/home.php"]
http://www.videotutorialsrock.com/opengl_tutorial/crab_pong/home.php[/URL]

So far I've
 sudo apt-get install freeglut3 freeglut3-devD

And in my build options I'm getting.
-L/usr/lib -L/usr/X11/lib  -lGL -lGLU

I'm compiling ok but I'm getting these errors:

```
obj/Debug/gamedrawer.o||In function `(anonymous namespace)::loadTexture(Image*)':|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|81|undefined reference to `glGenTextures'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|82|undefined reference to `glBindTexture'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|90|undefined reference to `glTexImage2D'|
obj/Debug/gamedrawer.o||In function `GameDrawer::setupBarriers()':|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|164|undefined reference to `glGenLists'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|165|undefined reference to `glNewList'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|168|undefined reference to `glEnable'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|169|undefined reference to `glBindTexture'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|170|undefined reference to `glTexParameteri'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|171|undefined reference to `glTexParameteri'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|174|undefined reference to `glMaterialfv'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|176|undefined reference to `glNormal3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|177|undefined reference to `glBegin'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|178|undefined reference to `glTexCoord2f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|179|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|182|undefined reference to `glTexCoord2f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|185|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|187|undefined reference to `glEnd'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|191|undefined reference to `glMaterialfv'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|193|undefined reference to `glDisable'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|194|undefined reference to `glColor3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|195|undefined reference to `glNormal3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|196|undefined reference to `glBegin'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|197|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|200|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|202|undefined reference to `glEnd'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|205|undefined reference to `glBegin'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|208|undefined reference to `glNormal3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|210|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|213|undefined reference to `glVertex3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|215|undefined reference to `glEnd'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|216|undefined reference to `glEndList'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|221|undefined reference to `glGenLists'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|222|undefined reference to `glNewList'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|223|undefined reference to `glDisable'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|227|undefined reference to `glMaterialfv'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|228|undefined reference to `glMaterialf'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|232|undefined reference to `glPushMatrix'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|233|undefined reference to `glTranslatef'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|234|undefined reference to `glCallList'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|235|undefined reference to `glPopMatrix'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|238|undefined reference to `glEnable'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|243|undefined reference to `glMaterialfv'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|244|undefined reference to `glMaterialfv'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|246|undefined reference to `glEndList'|
obj/Debug/gamedrawer.o||In function `GameDrawer::setupPole()':|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|250|undefined reference to `glGenLists'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|251|undefined reference to `glNewList'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|252|undefined reference to `glDisable'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|253|undefined reference to `glColor3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|256|undefined reference to `glNormal3f'|
/home/jonas/crab_game/crab_game/gamedrawer.cpp|257|undefined reference to `glBegin'|
||More errors follow but not being shown.|
||Edit the max errors limit in compiler options...|
||=== Build finished: 50 errors, 0 warnings ===|
```

I think I'm missing linking to a library but I'm not sure what's going on

If I highlight and go to declarations for  'glGenTextures' the code::blocks ide takes me to:
```
GLAPI void GLAPIENTRY glGenTextures( GLsizei n, GLuint *textures );
```

in gl.h.
So it think I'm missing something obvious here.  I've google'd posted on 
[http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=292947#Post292947]("http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=292947#Post292947")
(so far no response).
I don't understand the error.. Any thoughts?

---

### Post by Jonas thomas on 2011-03-06
me bad... forgot to set my linker options in code::blocks..
On to the next error...

The correct settings for the linker are -lGL -lGLU -lglut

btw... If anyone wants to play around with this tutorial in ubuntu.
I did a little post on my blog [http://www.metalshaperman.com/?p=631]("http://www.metalshaperman.com/?p=631")

---

### Post by glarrain on 2011-05-19
> **Jonas thomas said:**
> 
The correct settings for the linker are -lGL -lGLU -lglut


Thanks Jonas. I was stuck trying to run my first application using ODE and its own graphical library. -lGL and -GLU did the trick.

---

