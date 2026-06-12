---
title: "undefined reference"
date: 2006-04-03
forum: Programming Talk
---

### Post by Farbi on 2006-04-03
Hello all... 
New to linux here and I'm tring to get back into the programming thing... And after 8 straight hours of pulling my hair out I'm completly bald :~)  

My question is what am I doing wrong... I have various ideas about what it is that I'm missing, however have no idea how to fix them.

a little pre-info
Trying to learn openGL using C, C++ as a language
I've looked at various Tutorials and followed them to the best of my ability.
I've tried tutorials that use various different headers from redbooks aux.h to one that used glut.h
 I have all of that set up and going and none of the sources that I have written, or copy/paste have a problem compiling.  when I build them the say undefined reference.

I'm thinking that maybe I don't have a library file linked right? or that maybe i'm missing something else entirely.  I've looked, searched the forums here but didn't see anything that really helped.  I also followed links that i thought might help but always with the same result.

IDE=anjuta, and\or Gedit/gcc
also tried doing the whole gcc and g++ thing.
I have build-essentials installed along with every mesa, libgl thing I can find in synaptic.


Any thoughts?

```
source:
#include <GL/gl.h> //include the gl header file
#include <GL/glut.h> //include the glut header file

void display (void) {
glClearColor (0.0,0.0,0.0,1.0); //clear the color of the window
glClear (GL_COLOR_BUFFER_BIT); //Clear teh Color Buffer (more buffers later on)
glLoadIdentity(); //load the Identity Matrix
gluLookAt (0.0, 0.0, 5.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0); //set the view
glFlush(); //flush it all to the screen
}

int main (int argc, char **argv) {
glutInit (&argc, argv); //initialize the program.
glutInitDisplayMode (GLUT_SINGLE); //set up a basic display buffer (only singular for now)
glutInitWindowSize (500, 500); //set whe width and height of the window
glutInitWindowPosition (100, 100); //set the position of the window
glutCreateWindow ("A basic OpenGL Window"); //set the caption for the window
glutDisplayFunc (display); //call the display function to draw our world
glutMainLoop (); //initialize the OpenGL loop cycle
return 0;
}
```

output of gcc -o Hello_World world.c:

```
/tmp/cc67hodz.o: In function `display':
world.c:(.text+0x1f): undefined reference to `glClearColor'
world.c:(.text+0x2f): undefined reference to `glClear'
world.c:(.text+0x37): undefined reference to `glLoadIdentity'
world.c:(.text+0xab): undefined reference to `gluLookAt'
world.c:(.text+0xb3): undefined reference to `glFlush'
/tmp/cc67hodz.o: In function `main':
world.c:(.text+0xe0): undefined reference to `glutInit'
world.c:(.text+0xed): undefined reference to `glutInitDisplayMode'
world.c:(.text+0x102): undefined reference to `glutInitWindowSize'
world.c:(.text+0x111): undefined reference to `glutInitWindowPosition'
world.c:(.text+0x121): undefined reference to `glutCreateWindow'
world.c:(.text+0x131): undefined reference to `glutDisplayFunc'
world.c:(.text+0x139): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status
```

output of  gcc -o Hello_World world.c -lX11 -lMesaGL -lMesaGLU -lMesatk -lm
(as per another tutorial I followed):

```
/usr/bin/ld: cannot find -lMesaGL
collect2: ld returned 1 exit status
```

and anjuta produces the same thing as the gcc -o Hello_World world.c

any help would be really REALLY appreciated.

and if you need any other info i'll be happy to let you know.  so long as you tell me how to obtain this info (i.e version numbers and the like)


Thanks in advance 
Farbish

---

### Post by hod139 on 2006-04-03
Have you tried:
```

gcc -o world world.c -lGL -lGLUT 
``` 
**Edit:**  I should add, if you need GLU you would use -lGLU.  The flag -lm is only needed if you are using the math library.

---

### Post by Farbi on 2006-04-03
Wow, thanks for the quick responce... Unfortunatly it did not work either :~(

Output of  gcc -o world world.c -lGL -lGLUT
```
/usr/bin/ld: cannot find -lGLUT
collect2: ld returned 1 exit status
```


any other ideas?

Farbish

P.S. (edit)  I noticed that it didn't say cannot find -lGL... is there a way to install -lGLUT?  for that matter how/where would I find it and also how would I go about installing it?  is it simple apt-get thing or something a little more hairy like make, make prepare etc etc....?

Again thanks for the speedy responce
Farbish

---

### Post by hod139 on 2006-04-03
Oops, my bad:oops:.  glut should not be capitalized like the others.   It should be:
```

gcc -o world world.c -lGL -lglut 

```

EDIT:  Missed your second question.  To make sure glut is installed type
```

sudo apt-get install freeglut3-dev

```

---

### Post by Farbi on 2006-04-03
woot!!! thank you very Very much.  I feel so much better now.  It worked.    Thank you so much  now to find that tutorial again(i closed it in frustration :~)
I'll probably be back with more questions :~)

Thanks again
Farbish

---

