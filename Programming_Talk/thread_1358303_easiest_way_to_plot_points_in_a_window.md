---
title: "easiest way to plot points in a window?"
date: 2009-12-18
forum: Programming Talk
---

### Post by mlevin77 on 2009-12-18
Using C code, what's the easiest way to open a window, establish coordinates of say, 100x100, and plot points on it in a simple way (e.g., "plot(50,50)" to put a dot in the middle of the screen)? What package/tool will get me there fastest, without having to mess around with low-level window GUI calls, etc. - what do I install so that I can make simple plots from C?

---

### Post by unknownPoster on 2009-12-18
SDL isn't terribly complicated.

I used it rather extensively during my past semester at school. You may enjoy it.

[http://www.libsdl.org/](http://www.libsdl.org/)

---

### Post by mlevin77 on 2009-12-18
> **unknownPoster said:**
> SDL isn't terribly complicated.

I used it rather extensively during my past semester at school. You may enjoy it.

[http://www.libsdl.org/](http://www.libsdl.org/)

 great, thanks!  I'm using eeeBuntu (a variant of Ubuntu for the eeePC netbook). What do I need to grab to be able to use this library? Do I need to compile everything from scratch and if so, what's the most compatible source code version?  Are there simple examples of code that opens a window, defines virtual coordinates (say, 100x100) and plots some points? I'll go through the manual but if there's a link you know of, I'd love to see it. 

thanks,

Mike

---

### Post by unknownPoster on 2009-12-18
As far as I know, the SDL libraries are in the Ubuntu repositories. I would look for libsdl within synaptic.

---

### Post by mlevin77 on 2009-12-18
super, thanks!   I'm missing something basic though. In the example at

[http://www.libsdl.org/intro.en/usingvideo.html](http://www.libsdl.org/intro.en/usingvideo.html)

in the DrawPixel function, I see a pointer to the screen to use, and a color R,G,B triplet. Fine; but where are the coordinates at which to put the dot?  And where does one set the virtual coordinates (to say I want the X axis numbered from -100 to 100, or from 0 to 1000, or whatever).

thanks again,

Mike

---

### Post by unknownPoster on 2009-12-18
At the end of that function:

```
SDL_UpdateRect(screen, x, y, 1, 1);
```

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_UpdateRect](http://www.libsdl.org/cgi/docwiki.cgi/SDL_UpdateRect)

---

### Post by mlevin77 on 2009-12-18
I must be losing it - sorry if this is a stupid question.  The UpdateRect docs say the x,y tell it which portion of the screen to update, but where do we tell it where the dot I placed prior to the updating goes? And, is there any way to control the size of the "dot" (suppose I want to place a * character at those coordinates, or a small circle or whatever)?  

Mike

---

### Post by unknownPoster on 2009-12-18
> **mlevin77 said:**
> I must be losing it - sorry if this is a stupid question.  The UpdateRect docs say the x,y tell it which portion of the screen to update, but where do we tell it where the dot I placed prior to the updating goes? And, is there any way to control the size of the "dot" (suppose I want to place a * character at those coordinates, or a small circle or whatever)?  

Mike

That's a huge open-ended question. :P

If you wanted to place a * somewhere, you could look into using the SDL_ttf library.

To be completely, honest, I haven't really used SDL for direct drawing. I had to develop a 2-dimensional game engine in one of my classes this past semester.

We created sprites before hand, and then place them on the screen at specified x and y coordinates.

However, the drawpixel function that you are looking at is actually "drawing" on the screen. Well, to be more precise, it is changing the color of the specified pixel to whatever color is specified.

---

