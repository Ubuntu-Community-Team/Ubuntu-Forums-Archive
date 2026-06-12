---
title: "Drawing single pixel (again...)"
date: 2012-01-02
forum: Programming Talk
---

### Post by jpka on 2012-01-02
Hi!
I just need to draw single pixel(s) in my GTK C application.
Pixel values arrives during program runtime, so it can't be drawn as image or other predefined array.

I was use **gdk_draw_point()** before, and it was worked like a charm.
But now i read on *gnome.org*
> Warning
gdk_draw_point has been deprecated since version 2.22 and should not be used in newly-written code. Use cairo_rectangle() and cairo_fill() or cairo_move_to() and cairo_stroke() instead. 

I turn to Cairo, but drawing single pixels in it is not allowed, it emulates it by drawing unity lines or rects. I do it, but it working incredibly slow: **cairo_rectangle()** at least 10000 times slower than **gdk_draw_point()**. It is unacceptable.

I then found function [here (scroll to Example 1)]("http://developer.gnome.org/gdk-pixbuf/stable/gdk-pixbuf-The-GdkPixbuf-Structure.html"), but i unfortunately can't imagine how to use it, i'm too novice in C. I search on web about GdkPixbuf examples, but found almost nothing. 

Q1: Is mentioned function is not deprecated?
Q2: It there a simple example exist anywhere how to use this function?
Q3: Is any other ways do draw single pixels exist? (i mean not really slow ones).

When i draw my first pixels in BASIC 20 yrs ago, i newer can't imagine that in 21th century it becomes the huge world-wide problem.

Thank you very much! ;)

---

### Post by xytron on 2012-01-02
As far as I can tell all the GDK drawing functions are deprecated since GTK+ 3.0  they are now replaced by Cairo drawing functions.

If cairo_rectangle() is too slow maybe you can draw your image with the move_to(), line_to() and stroke() functions instead.

I did a test with the following image drawn using only move_to() and line_to() and Cairo draws it very fast (granted it's not a very complicated image)

[IMG]http://www.allthewonder.com/waves01.png[/IMG]

I'm just curious what exactly are you trying to do that you need to light up individual pixels?

Usually drawing lines or polygons is faster than just lighting up pixels.


You could also just skip GTK+ altogether and just use Xlib directly to draw pixels by using the XPutPixel() function to set a pixel value in an image ( of type XImage).

Also there is  a C++ library for creating png images called PNGwriter which will will let you easily set pixels on a png image drawing surface, it is very simple to use and it is fast.

Another way to do it is just to use libpng directly yourself.

libpng is the official PNG library.  It's platform independent and supports all of PNG's features.

To create your image with libpng just create a rectangular array that represents your image surface pixel colours to be written out as a PNG image, I think this will be the fastest method if you have lots of pixel data.

The FLK gui toolkit is another option which will let you draw pixels.  Even OpenGL is an option if you really have to.

I would suggest just using Xlib,  PNGwriter or libpng (libpng is probably the solution that will produce the faster executable)  if you don't want to use Cairo.
 
So you see there actually are quite a few options for you, and there probably are others that I'm not even aware of.

---

### Post by jpka on 2012-01-03
Hi! 
> **xytron said:**
> I'm just curious what exactly are you trying to do that you need to light up individual pixels?
One example of this is my open-source EEPROM Ethernet programmer, please see screenshot. It definitely need to draw each individual pixel (which represents a piece of data in chip) without delay when programming, because it can show quality of the EEPROM chip. So buffering or any other aggregating pixels before display it all as one image is not allowed. 
Another example is my software oscilloscope and VSWR meters (open-source but still beta), when 50-60 fps in 512*512 window is essential, and gdk_draw_point() doing it with ease.
I read your ideas and possible ways of drawing. While some is file-related, not screen-related, like libpng, you also mentioned openGL which is very good idea because it is screen-related and hardly optimized for performance. I will immediately start to test openGL. But if i suddenly find pixel-related examples for other on-screen ways of fast drawing, or if you suggest me these examples, i will of course test it also :-)

Thank you very much! :KS
And i become even more happy if i maybe can find answers on my questions Q1, Q2. :-)

---

### Post by xytron on 2012-01-04
The gdk-pixbuf is a toolkit for image loading and pixel buffer manipulation I don't think that is what you are looking for.
 
Xlib or OpenGL seem to be the choices.
 
Xlib will allow you to manipulate pixels directly in a window or even on the desktop itself.
With Xlib your solution is tied to Linux/Unix if you care about platform independent code (and we always ought to). Plus interfacing your GTK+ windows with your Xlib windows will just complicate things a bit.
 
OpenGL may be the best choice, it's easy to draw pixels in an OpenGL window. Since you are using GTK+ you'll probably have to use a library to interface to OpenGL (such as gtkglext).
 
I've put together an example OpenGL program to draw pixels. It looks a little long but that is because only Xlib is used to create the OpenGL window (with GLX).
The program uses Xlib with OpenGL there are no other library dependecies.
 
It's quite simple, it only draws a red pixel at the center of the window.
 
You light up pixels at (x,y) with the setPixel function;
 
setPixel(x,y,r,g,b)
 
Just put the drawing code in the Draw() function.
 
[URL="http://www.allthewonder.com/linux.html"]gl-points.c
[/URL]

---

### Post by jpka on 2012-01-04
> **xytron said:**
> gl-points.c
Hi Xytron!
Thank you so much for writing this example code! It is very important to me.
I compile and run it well. Then i try to test performance.
What i do next: 
1. move glClear() to outside of setPixel() so i now able to draw multiple pixels.
2. Resize window to 512*512. Set pixel size to 1.0.
3. Modify draw() like this:
```
void draw(Display *display, Window win) {
	glClear(GL_COLOR_BUFFER_BIT);
	int i;
	for (i=0; i<10000000; i++) {
		setPixel(rand()%512,rand()%512,(rand()%256)/256.0,(rand()%256)/256.0,(rand()%256)/256.0);
//		glXSwapBuffers(display, win);
	}
	glXSwapBuffers(display, win);
}

```
and it takes ~1.5 second to draw ten millions of pixels into internal buffer then show it at once.
But i need on-screen drawing, not into buffer. Then only i can do is move glXSwapBuffers() into loop. Drawing only 10000 pixel (1000 times less) takes 5 seconds :confused:
Where am i wrong? Can i draw directly onto screen using openGL? Thank you *very* much for your help and examples! ;) :KS

(edit: i think if i can tie glXSwapBuffers() to vertical screen refresh signal, it solves all performance issues, but i have no idea how to do it)

---

### Post by xytron on 2012-01-04
I ought to have seen it OpenGL won't work for you.
 
OpenGL doesn't provide a standard way that lets an application get the address of the framebuffer. 
 
There was a video synchronization extension to OpenGL from SGI that's all I know about it.
 
gdk basically just uses the standard Xlib function calls, so you could just look at the source code to see how they implemented the gdk_draw_point() function that you were using.
 
The advantage of gdk is that it is cross platform, that is it's a wrapper around Xlib.
 
I wrote a small Xlib program to draw the 10 million pixels directly into an X window using the XDrawPoint() function;
 
[pixels.c]("http://www.allthewonder.com/linux.html")
 
I still think there is a possibility this could be done with Cairo, but haven't explored it.

---

### Post by jpka on 2012-01-09
> **xytron said:**
> pixels.c

It is amazing! :D
While i still can't draw any colored pixel with it, even after some days, but your example shows outstanding drawing performance, and it is small but powerful - it is very important for me. It also probably uses lowes possible layer while still maintaining interoperability, it is very good and rare thing.
Thank you so much for your help! :KS :KS :KS :KS :KS I will continue to deep study it and used functions.

---

### Post by jpka on 2012-01-09
I also try to find and use 'video synchronization extension to OpenGL'. While openGL's site does not provide any simple example of video synchronization, and i can't find it in simple form elsewhere, i still notice that 'Video Sync' openGL option im my Nvidia control panel does make sense: glXSwapBuffers() now waits for vertical retrace. But wait periods in my software is not allowed. So the solution i think is push out glXSwapBuffers(), in form like this: ```
		while (1) { glXSwapBuffers(display, win); }

```, to standalone thread or process. The problem is i too weak in C programming, i am very sorry for it... I search about parallel multitasking and found two ways how to run parallel processes, these are threads and fork(). 
I try to using threads and find simple example [here]("http://timmurphy.org/2010/05/04/pthreads-in-c-a-minimal-working-example/"). But when i write my thread function as mentioned above, i.e. when thread never returns, main program also locks up. So i see that threads are not parallel tasks, unfortunately.
I also try to use fork(), but i can't imagine how to create parallel process using it, because it looks to be used to run parallel executable files but not functions.
If i find in future how to run endless parallel process, which not blocks main process, it may be looks useful and then i maybe able to use openGL.

---

### Post by t1497f35 on 2012-01-09
I think you should post your app source code and how to compile & run it, it will allow people to actually test what you're doing and provide real solutions known to run well in your case.

Using OpenGL to draw 10 000 000 pixels should only take a tiny fraction of a second, since ten mission * 3 bytes per pixel (RGB) is only about 28MB of (video graphics) RAM.

That's if you use FBOs (framebuffer objects), however, if you use the fixed (old) OpenGL function pipeline then of course it will be slow as hell and take like a second or more. Of course, if you have OpenGL version < 2.1 then it probably won't run. From the screenshot looks like you're also running an old version of Ubuntu.

Also, you have to learn/know OpenGL which might take a few months.

---

### Post by xytron on 2012-01-09
> **jpka said:**
> It is amazing! :D
While i still can't draw any colored pixel with it, even after some days, but your example shows outstanding drawing performance,

I've put another small example Xlib program to draw pixels with colour, it draws red pixels on a black background with a blue border around the window.

[pixels-colour.c]("http://www.allthewonder.com/linux.html")

Using colours with Xlib is not as bad as some say if you use the default colour map, and mostly that's the one to use.

Remember this is a very simple example in a useful program you'll also have to redraw the screen, handle window events etc...

---

### Post by jpka on 2012-01-18
> **xytron said:**
> pixels-colour.c

Hi! I am very sorry for my delay, but currently the file is not exist :( . Can you please repeat, or send me it via PM? Thanks! :)

(P.S. I'm actively working on my software, so very sorry for my delays)

---

### Post by jpka on 2012-01-18
> **t1497f35 said:**
> I think you should post your app source code and how to compile & run it

I will do it very soon, the code needs a bit cleanup from my strange writing "style". But unfortunately i think this code almost does not make sense because it can work only with my hardware, so almost can't be tested by other friends. My hardware (for EEPROM programmer) is also open-source and built mainly using W5100 & ATMEGA32A, but need cleanup again. I was design it as simple as possible, so it will be useful by as many people as possible. I will post it all soon. Thank you all very much for your help! :)

---

### Post by t1497f35 on 2012-01-18
> **jpka said:**
> I will do it very soon, the code needs a bit cleanup from my strange writing "style". But unfortunately i think this code almost does not make sense because it can work only with my hardware, so almost can't be tested by other friends. My hardware (for EEPROM programmer) is also open-source and built mainly using W5100 & ATMEGA32A, but need cleanup again. I was design it as simple as possible, so it will be useful by as many people as possible. I will post it all soon. Thank you all very much for your help! :)
Well, then I don't zaviduiu you since to run the sw one needs custom hw, hence few people to come up with stuff proven to work on your hw.

---

