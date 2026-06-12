---
title: "Starting to program with C/C++ and OpenGL"
date: 2007-03-03
forum: Programming Talk
---

### Post by Arlanthir on 2007-03-03
First off, I want to state I'm not sure whether I should be posting this here, but I found no better candidate, so as this is really beginner's stuff I decided I should try my luck here, even though searches for this came with no good results...

I'm trying to start checking some OpenGL tutorials to see how far I can go in 3D Development, my first goal being actually compiling something.. This is proving to be quite a task, because I decided to try ubuntu a few weeks ago and I'm no pro at it, even though I'm loving the experience (I hardly log into windows now), so despite having typed (as found in a thread somewhere in this forum answering to a similar question)  ```
sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev
``` I cannot run cogl, having the error ```
bash: cogl: command not found
``` I'd like to know what I'm doing wrong and hopefully a way to do it right!

I expect this to be a no-brainer, so I hope you bare with my noobness =P
Thank you very much!

EDIT: It came to my attention that COGL is in fact a way some university has of compiling OpenGL code.. They made a manual and such.. And following it I came across the cogl command.
You can find it [here]("http://www.cs.manchester.ac.uk/software/OpenGL/opengl.pdf").

So, how should I try to compile an example? I suppose it should be gcc with some library parameters, right?
If you have handy examples that could help me, please give me some pointers.

Again, thank you very much!

---

### Post by K.Mandla on 2007-03-03
(Hi. I'm just going to shift your thread to the Programming forum, where it will probably attract more attention from people who can help you. ;) )

---

### Post by Arlanthir on 2007-03-03
Thanks, I didn't know where to post it!

---

### Post by Wybiral on 2007-03-03
OK, here's a very simple GLUT + OpenGL program:
```

#include <GL/glut.h>


#define window_width  640
#define window_height 480

// Main loop
void main_loop_function()
{
   // Z angle
   static float angle;
   // Clear color (screen) 
   // And depth (used internally to block obstructed objects)
   glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
   // Load identity matrix
   glLoadIdentity();
   // Multiply in translation matrix
   glTranslatef(0,0, -10);
   // Multiply in rotation matrix
   glRotatef(angle, 0, 0, 1);
   // Render colored quad
   glBegin(GL_QUADS);
   glColor3ub(255, 000, 000); glVertex2f(-1,  1);
   glColor3ub(000, 255, 000); glVertex2f( 1,  1);
   glColor3ub(000, 000, 255); glVertex2f( 1, -1);
   glColor3ub(255, 255, 000); glVertex2f(-1, -1);
   glEnd();
   // Swap buffers (color buffers, makes previous render visible)
	glutSwapBuffers();
   // Increase angle to rotate
   angle+=0.25;
}

// Initialze OpenGL perspective matrix
void GL_Setup(int width, int height)
{

	glViewport( 0, 0, width, height );
	glMatrixMode( GL_PROJECTION );
	glEnable( GL_DEPTH_TEST );
	gluPerspective( 45, (float)width/height, .1, 100 );
	glMatrixMode( GL_MODELVIEW );
}


// Initialize GLUT and start main loop
int main(int argc, char** argv) {
	glutInit(&argc, argv);

	glutInitWindowSize(window_width, window_height);

	glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE);

	glutCreateWindow("GLUT Example!!!");

	glutIdleFunc(main_loop_function);

	GL_Setup(window_width, window_height);
   glutMainLoop();

}

```

It's a rotating quad.

You need to save that as "something.cpp"

And compile it from the command line with...

```

g++ something.cpp -lglut

```

And there you go!

BTW, I highly advise SDL over GLUT.

Also, if you need some good tutorials and examples:
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)
is the place to go (lots of linux examples to download too!)

Good luck!

---

### Post by lnostdal on 2007-03-03
just a short note; a good habit is to add the -Wall and -g arguments while doing development (remove -g when you want a release-build)

-Wall helps point out potential problems, and -g will help the debugger help you

---

### Post by Arlanthir on 2007-03-04
@ Both

W00t! :D
Worked like a charm, -Wall and -g gave no output too, so I'm thinking no warnings of any sort =) Thank you! 

@ Wybiral

What is SDL and what are the differences? I'm extremely new to this, so I'm just really following instructions..

---

### Post by Wybiral on 2007-03-04
> **Arlanthir said:**
> @ Both

W00t! :D
Worked like a charm, -Wall and -g gave no output too, so I'm thinking no warnings of any sort =) Thank you! 

@ Wybiral

What is SDL and what are the differences? I'm extremely new to this, so I'm just really following instructions..

OK... In the same way that you use GLUT to initialize a window and do things like handle user events (mouse/keys) you can use SDL for the same thing.

The main reason I advocate SDL over GLUT is this:
```

   glutIdleFunc(main_loop_function);
   glutMainLoop();

```
You have to pass a function to GLUT and then call "glutMainLoop()"
This hands the program flow over to GLUT so certain things can't be done, meaning: sometimes you can't incorporate a system that requires letting GLUT take over.

SDL on the other hand is very different... It doesn't control the program flow so it's up to you. SDL also has better mouse and key functions and it's even handling system is very easy to use. SDL also has several helper libraries like: SDL_image (which helps you load various image formats for use in SDL and OpenGL), SDL_net (a networking library), as well as other libraries for 2d graphics too.

Here's a modified SDL version of that GLUT demo:

```

#include <GL/gl.h>
#include <GL/glu.h>
#include <SDL/SDL.h>

#define window_width  640
#define window_height 480

// Keydown booleans
bool key[321];

// Process pending events
bool events()
{
   SDL_Event event;
   if( SDL_PollEvent(&event) )
   {
      switch( event.type )
      {
         case SDL_KEYDOWN : key[ event.key.keysym.sym ]=true ;   break;
         case SDL_KEYUP   : key[ event.key.keysym.sym ]=false;   break;
         case SDL_QUIT    : return false; break;
      }
   }
   return true;
}

void main_loop_function()
{
   float angle;
   while( events() )
   {
      glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
      glLoadIdentity();
      glTranslatef(0,0, -10);
      glRotatef(angle, 0, 0, 1);

      glBegin(GL_QUADS);
      glColor3ub(255, 000, 000); glVertex2f(-1,  1);
      glColor3ub(000, 255, 000); glVertex2f( 1,  1);
      glColor3ub(000, 000, 255); glVertex2f( 1, -1);
      glColor3ub(255, 255, 000); glVertex2f(-1, -1);
      glEnd();

   	SDL_GL_SwapBuffers();
      // Check keypresses
      if( key[SDLK_RIGHT] ){ angle-=0.5; }
      if( key[SDLK_LEFT ] ){ angle+=0.5; }
   }
}

// Initialze OpenGL perspective matrix
void GL_Setup(int width, int height)
{
   glViewport( 0, 0, width, height );
   glMatrixMode( GL_PROJECTION );
   glEnable( GL_DEPTH_TEST );
   gluPerspective( 45, (float)width/height, 0.1, 100 );
   glMatrixMode( GL_MODELVIEW );
}

int main()
{
   // Initialize SDL with best video mode
   SDL_Init(SDL_INIT_VIDEO);
   const SDL_VideoInfo* info = SDL_GetVideoInfo();	
   int vidFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;
   if (info->hw_available) {vidFlags |= SDL_HWSURFACE;}
   else {vidFlags |= SDL_SWSURFACE;}
   int bpp = info->vfmt->BitsPerPixel;
   SDL_SetVideoMode(window_width, window_height, bpp, vidFlags);

   GL_Setup(window_width, window_height);

   main_loop_function();
}

```

I added some extra stuff to show how you could process key events (as well as window exit's because SDL does NOT close the window for you, you have to end the loop)

You can compile that with:
```

g++ something.cpp -lSDL -lGLU -lGL

```

Also, as I mentioned SDL_image... You can find it in synaptic too, it makes texture loading VERY VERY easy (including: bmp, png, gif, jpg, pcx...)

---

### Post by Arlanthir on 2007-03-04
Well, I guess I'll do it the way I'll learn in college O.o
Maybe try some of the examples, I have some plans =)

---

### Post by studiesrule on 2007-03-04
I also agree with Wyrbiral, that SDL makes life very very easy. NeHe's tutorials are excellent. Some other tutuorials you might find useful:

[Lazy Foo Prod.]("http://lazyfoo.net/SDL_tutorials/index.php") : Great for SDL, you wont need too much of it, except for texture loading and multithreading.

[Cone3d]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/index"): Some other 3d tutorials. It would be useful to you mainly for the loading of Quake2 models and octrees

[Lode's Computer Tutorials]("http://student.kuleuven.be/~m0216922/CG/index.html") : Some more advanced tutorials, with good end-to-end examples. You could try and apply your OpenGL knowledge here.

[OpenGL and SDL]("http://osdl.sourceforge.net/OSDL/OSDL-0.3/src/doc/web/main/documentation/rendering/SDL-openGL.html") : This has some information on how to use OpenGL with SDL. This is also mentioned in the Lazy Foo tutorials.

One important pointer is that NeHe's tutorials use the windows code, and if you look at it, you'll most proabably cower in fear, or laugh hysterically at the pain winProgrammers have to go through. Just understand that SDL takes care of all the memory allocations and creating resources for you. Look at the SDL examples at the bottom of the tutorials for some help on porting to SDL.

Also note that the SDL default has a slightly different coordinate system, and it's not hard to switch between the two, you just have to be aware of it. It will be mentioned on the other sites i've posted, but not on NeHe's page (so don't get frustrated if your textures load up awry)

Best of luck!

---

### Post by Arlanthir on 2007-03-04
Thank you all of you =) If I come up with something I'll show around :P
I'm planning on making my projects work in linux and windows, but it's going to take a while until I have something.. Very helpful of you, though, I appreciate it!

---

### Post by phorgan1 on 2007-06-19
> **Arlanthir said:**
> @ Both

W00t! :D
Worked like a charm, -Wall and -g gave no output too, so I'm thinking no warnings of any sort =) Thank you! 

@ Wybiral

What is SDL and what are the differences? I'm extremely new to this, so I'm just really following instructions..

SDL is a 2d portible graphics library that can provide a framework for OpenGL programming.  It 
provides access to keyboards and mice and joysticks etc.  

I'm working on a C++ framework similar to glut (I steal it's user interface brazenly;).  I also add other stuff, like through the TTF librarie's I make it possible to do general purpose OpenGL text.  I use that facility to provide a general menu interface that goes way beyond what glut provides.  I still have a lot of work to do on it, but I'm looking for people that want to thrash it and rewrite it and check out the portability of it.  I work on Linux, but I only use facilities of SDL and OpenGL, both of whom are portable across many platforms, so I have hope:)

I could modify it to be C pretty easily, but I think in objects so I figured I'd get it a lot more developed before I do that.

patrick -- phorgan1 at gmail dot com

---

### Post by Arlanthir on 2007-06-20
Thank you for the explanation! =)
I better wait a year or so until I start attending classes for opengl and graphical computation =/

---

### Post by new_to_ubunt_u on 2011-02-14
Hello,

tried your code but it erred out.

The error displayed is

/tmp/ccKWyKs5.o: In function `GL_Setup(int, int)':
one.cpp:(.text+0x1bc): undefined reference to `gluPerspective'
collect2: ld returned 1 exit status

It might be an extremely stupid thing.. am new so please help. thanks

---

### Post by uRock on 2011-02-15
Please start a new thread. This one is old. Very, very old.

---

