---
title: "Early Alpha of Slides (AKA GtkPresentationProgram)"
date: 2009-02-23
forum: Programming Talk
---

### Post by tom66 on 2009-02-23
I've been working hard on getting this very early beta of my presentation program (Slides) working. Here's what works:

 - Zooming up to 20x and as low as 0.1x. Text currently modifies the size to zoom; I am planning to potentially change this because of problems with hinting when this is done. 
 - Viewport scrolling, though this could do with a few fixes.
 - Text rendering with multiple styles, a text area can have bold and italic text, for example.
 - Object rendering.
 - Canvas rendering.
 - Fits to canvas; the program will try to adjust the viewport so that you see the same stuff as you would at a higher resolution, just in a smaller space.
 - Basic GTK interface: A toolbar with zoom options, and two scrollbars.
 - It's also quite fast for a Python app. Not quite as fast as C, but easier to develop and the slight loss of speed is fine for this program. 

You can't yet use it to edit anything, but it's a good start I think. 

Let me know what you think. I attach a .tar.gz of the files you need for the program, but you'll also need Python, PyGTK, PyCairo, Cairo, Pango and PangoCairo installed. (These are installed on a vanilla Ubuntu install already.)

Run by typing 'python main.py' from a command line. 

I've also committed the code to [https://launchpad.net/gtkpresentationprogram-python](https://launchpad.net/gtkpresentationprogram-python)

Enjoy, and please give me your comments!

---

### Post by Tomosaur on 2009-02-23
Looks pretty good, although you could do with a bit more information in the launchpad page so people know exactly what it's supposed to do.

Also, I assume the intention is to support some file format(s) eventually?

---

### Post by tom66 on 2009-02-23
Yes, first a native .slides format and eventually OpenDocument Presentation and Microsoft PowerPoint Presentation & Show (.pps is like .ppt, except it can't be edited). But first, I need to get editing and the interface working and then animation.

---

