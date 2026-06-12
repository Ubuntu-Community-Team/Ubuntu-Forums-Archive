---
title: "making an openGL program output a jpg"
date: 2007-12-31
forum: Programming Talk
---

### Post by troxy18 on 2007-12-31
I have a written a program in OpenGL and GLUT in C++ that draws to the monitor plots of the Mandelbrot set, users can change the complexity and zoom in and such.  Is there a way to have OpenGL automatically output the image from the program to a jpg or some other image format?  I dont mean taking a screenshot since my code is buggy and crashes my X11 if windows are drawn over it sometimes.  

Here is a screenshot I was able to take of my program.  To take his I had to dial the complexity way down, set up a time delay screenshot and then increase the complexity and not touch it until the screenshot takes and then save it and let it redraw before quitting the program.
[[IMG]http://img181.imageshack.us/img181/2036/screenshottroyfostersmamn9.png[/IMG]](http://imageshack.us)

---

### Post by Wybiral on 2008-01-01
I don't know of any APIs that do this for you, but it's pretty trivial yourself. Use [glReadPixels]("http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/readpixels.html") to read the screen into a buffer of the RGB, then use your favorite image API to save that buffer as a JPG.

---

### Post by troxy18 on 2008-01-01
If you could provide a code sample as a push it would be appreciated.

---

### Post by Wybiral on 2008-01-01
Supposing your window dimensions were 128x64, you could capture the entire rendered screen using:

```

unsigned char image[128 * 64 * 3];
glReadPixels(0, 0, 128, 64, GL_RGB, GL_UNSIGNED_BYTE, image);

```

Now that you have an array with each pixels RGB, you can use an image library to save it. I don't know of any image libraries, so I can't help there (but I do know there are plenty of them out there), they should have the ability to either specify a buffer of RGB (which you have) or plot each pixel (which you can do from the array above).

---

### Post by stroyan on 2008-01-01
glReadPixels does not guarantee reading from obscured pixels of a window.
To get reliable values you need to draw to and read from something that cannot
become obscured.  You could use a pixmap or a pbuffer.  Unfortunately, GLUT
does not assist with rendering to such buffers.  You might use GLX calls on ubuntu releases.  Or you could look to SDL for an OS independent way to get an offscreen rendering buffer.

---

