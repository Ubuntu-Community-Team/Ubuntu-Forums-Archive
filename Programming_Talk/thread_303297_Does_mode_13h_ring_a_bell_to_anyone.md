---
title: "Does mode 13h ring a bell to anyone?"
date: 2006-11-20
forum: Programming Talk
---

### Post by Peepsalot on 2006-11-20
I remember back in the days of DOS.  I could just set the video mode and start pushing pixels in a few lines of c++...or pascal.  Nowadays graphics just confuse the crap out of me.  Graphics libraries require dozens of arcane function calls just to initialize a display.  From the tutorials I have looked over, there are just too many hoops to jump through when you only want to make the simplest of graphics programs.

I just want to know what people would consider the simplest method of displaying some pixels these days.

---

### Post by amo-ej1 on 2006-11-20
Hehe, yeah i kinda agree with you but on the other end most libraries offer a great added value .... so you might feel like drowning in them at first but in the end you'll gain a lot of time using them.

Nevertheless, i'm also interested in any responses on your question. Personally i'd start to think in the direction of the framebufferdevice where something like: 
[www.linux-magazine.com/issue/03/EmbeddedGraphics.pdf](www.linux-magazine.com/issue/03/EmbeddedGraphics.pdf)
offers some basic info ...

---

### Post by fct on 2006-11-20
I come from those days too. Inputting assembly into turbo pascal code was kind of fun.

Try this library: [http://www.libsdl.org](http://www.libsdl.org)

With the SDL_Surface structure you get the "pixels" pointer to the pixel data so you can play around with direct pixel rendering. And it includes some nifty functions to blit, plus you can use OpenGL.

It's also quite easy to use and multiplatform, so if you want to do some simple graphics programming I suggest you use it.

---

### Post by hod139 on 2006-11-20
What language do you want to develop in?  C and C++ have SDL as someone else mentioned.  They also have OpenGL, of course you will need some sort of window: e.g. glut, fox, or wx.

Also, is cross platform building a concern?  

Will you eventually want to do other graphics related stuff, or do you really only ever want to dump pixels to the screen buffer?

---

### Post by coder_ on 2006-11-20
Hee hee, I remember well... kind of...  As in coding demos in assembler for DOS last year...
Too bad I missed the Amiga demoscene era...

---

### Post by Peepsalot on 2006-11-20
> **hod139 said:**
> What language do you want to develop in?  C and C++ have SDL as someone else mentioned.  They also have OpenGL, of course you will need some sort of window: e.g. glut, fox, or wx.

Also, is cross platform building a concern?  

Will you eventually want to do other graphics related stuff, or do you really only ever want to dump pixels to the screen buffer?
Well, I was messing with my cell phone and found the directory of animations on it.  The animations are in files with a .PAF extension.  I couldn't find any info on this extension, but I believe is is something close to raw image data for each frame in sequence.  I was going to see if I could just display the pixels from different sections of it so that i could visually see how the data is laid out.

---

### Post by hod139 on 2006-11-20
If you really think it is raw pixel data, here is some simple openGL and GLUT code that just require you getting the pixel data loaded.

```

#include <GL/glut.h>

#include <iostream>

// Missing global image data
unsigned char *image = 0; // image pixel data
int imageWidth = 1; // image width
int imageHeight = 1; // image height

/**
*Sets up approriate viewport coordinates for 2D
*/
void reshape(int w, int h)
{
   glViewport(0, 0, w, h);
   glMatrixMode(GL_PROJECTION);
   glLoadIdentity();
   glOrtho(0, w, h, 0, -1, 1);
   glMatrixMode(GL_MODELVIEW);
   glLoadIdentity();
}

/**
 * display callback function 
 */
void display(void){
    glClear(GL_COLOR_BUFFER_BIT);
    glDrawPixels(imageWidth, imageHeight, GL_RGB, GL_UNSIGNED_BYTE, image);
    glFlush(); 
}


/**
 * Main entry point
 */
int main(int argc, char *argv[]){
    
   //TODO: READ IMAGE DATA
   image = new unsigned char[0]; // Just so it doesn't segfaut when running with no image data

   // Initialize glut
   glutInit(&argc, argv);
   glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
   glutInitWindowSize(imageWidth, imageHeight);
   glutInitWindowPosition(100,100);
   glutCreateWindow("ImageLoading example");
   glutDisplayFunc(display);
   glutReshapeFunc(reshape);

   //for GL speed-ups
   glDisable(GL_DEPTH_TEST);
   glDisable(GL_ALPHA_TEST);

   // Override OpenGl's 4 byte boundary default 
   glPixelStorei(GL_UNPACK_ALIGNMENT, 1);

   glutMainLoop(); // Give control to glut

   exit(0);
}


```To compile
```

g++ foo.cpp -lglut

```All that you have to do is set the following values.
unsigned char *image, 
int imageWidth,
int imageHeight,

---

### Post by Mickeysofine1972 on 2006-11-22
Me and a couple of others are starting a game development series of HOWTO's startin with howto setup SDL for use with g++.

heres the link for the first one:

[http://www.ubuntuforums.org/showthread.php?p=1791682#post1791682](http://www.ubuntuforums.org/showthread.php?p=1791682#post1791682)

theres more to come soon!

Mike

---

### Post by Houman on 2006-11-22
Hi there;

Just for your info I have two code snippets that compare the old way of setting single pixels and the new way using some random library (here I use MFC, sorry)


The old way (setting a pixel to red at location x,y in mode 13):

```


unsigned char *VGA = (unsigned char*)0xA0000000L;
unsigned short offset; 
... 
offset = 320*y + x; 
VGA[offset] = 4; 

```

and the new way :


```

dc.SetPixel(x, y, RGB(255, 0, 0)); 

```

I know the comparison is a bit unfair, specially since setting a single pixel can be a bit more complicated in SDL (which is my favourite multimedia library) than MFC, but I think using a graphics library is much better than accessing hardware directly because you can create much more portable code (SDL is very cross platform) and also because you could really crash your OS if directly accessing hardware (thats why modern OS'es dont allow direct access to video hardware directly).

But anyhow if you like you can use the Linux's framebuffer as some people mentioned, thats as close as you can come to writing very low level code.

regards

Houman

---

