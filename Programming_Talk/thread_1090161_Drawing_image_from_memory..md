---
title: "Drawing image from memory."
date: 2009-03-07
forum: Programming Talk
---

### Post by Watashimo on 2009-03-07
'lo, all.

Newb to Linux GUI programming. Been looking around the internet all night for a way to simply draw a coloured bitmap, JPEG or GIF within a window... and I've found nothing. Well not necessarily nothing.

- I've found loads on Gdk/Gtk about drawing X bitmaps which are monochrome and I need full colour.

- Found some obscure references to "gdk-pixbuf" but cannot find it anywhere so I assume it's bundled with something rather than being stand-alone.

- Cairo... a) overkill and b) doesn't seem to have basic drawing capabilities.

So can someone please help me on the road to understanding how to draw a single image in a window - and any necessary libraries to do so?

Thanks in advance.

[edit]

Should probably note that I'm using C, but can use C++ if nesc.

---

### Post by Tony Flury on 2009-03-08
FYI : a gdk-pixbuf is a GDK object which can load images from file, and which other GTK widgets can then use to display that image. I am not sure if you can draw onto a pixbuf. There is also a GTK/GDK object called a Canvas (which I must be honest i have never used), which i beleive you can draw directly onto - with coloured pens etc.
Certainly from python a pixbuf is a standard part of the tool kit.

---

### Post by Watashimo on 2009-03-08
'ello. Thanks for the reply.

According to the code I found, you need to include gdk-pixbuf/gdk-pixbuf.h to use the functions. When I do that, it says it cannot find the headers... so I'm guessing I need to install something.

---

### Post by Gordon Bennett on 2009-03-08
[http://library.gnome.org/devel/gtk/stable/GtkDrawingArea.html]("http://library.gnome.org/devel/gtk/stable/GtkDrawingArea.html")

And
[URL="http://www.gtk.org/tutorial1.2/gtk_tut-23.html"]
http://www.gtk.org/tutorial1.2/gtk_tut-23.html[/URL]

Section 23.3

Also, make sure you have the development packages installed.

---

### Post by loell on 2009-03-08
you most likely need to install **libgtk2.0-dev**.

---

### Post by Watashimo on 2009-03-08
Ahoy.

Thanks for the two links. I had found them myself, but the problems are:

- With the first link, it tells you about this "GtkDrawingArea" but there's no info on all of the functions used to draw into it; it's just about the area itself with some examples.

- The 2nd link again seems to use shape-drawing functions (as does the first link use an arc drawing function) which is no use to me as I need to draw a set, fixed coloured bitmap.. in full image form (basically, a .bmp from memory). If possible, I'd rather use JPEG, but that might be more of a case of converting from JPEG to a bitmap/pixmap.

I do have GTK2 installed, but I'll check about the -devel package. I'm using GTK+ as GTK2 gave me errors about Pango which I don't understand... as both GTK2 and Pango have been installed using yum install.

Question: could I make a 600 x 480 pixel-by-pixel full colour image using pixmaps? It seems pixmaps are used for only small things like icons and I don't know whether a wide range of colours are available.

Thanks again.

---

### Post by simeon87 on 2009-03-08
> **Watashimo said:**
> 
- Cairo... a) overkill and b) doesn't seem to have basic drawing capabilities.


What do you mean, doesn't seem to have basic drawing capabilities? See [these samples](http://cairographics.org/samples/).. only a few lines needed to draw an image.

---

### Post by Watashimo on 2009-03-08
I meant that it seemed to be more for advanced 2D drawing instead of basic stuff. All I need to do is plot a very static image... although this "surface_create_from" stuff might be something I could use, but that'd require saving the data from memory into a file & then loading it back out which might be too costly (timewise).

---

### Post by Gordon Bennett on 2009-03-08
> **Watashimo said:**
> Thanks for the two links. I had found them myself, but the problems are:

- With the first link, it tells you about this "GtkDrawingArea" but there's no info on all of the functions used to draw into it; it's just about the area itself with some examples.

- The 2nd link again seems to use shape-drawing functions (as does the first link use an arc drawing function) which is no use to me as I need to draw a set, fixed coloured bitmap.. in full image form (basically, a .bmp from memory). If possible, I'd rather use JPEG, but that might be more of a case of converting from JPEG to a bitmap/pixmap.

I do have GTK2 installed, but I'll check about the -devel package. I'm using GTK+ as GTK2 gave me errors about Pango which I don't understand... as both GTK2 and Pango have been installed using yum install.

Question: could I make a 600 x 480 pixel-by-pixel full colour image using pixmaps? It seems pixmaps are used for only small things like icons and I don't know whether a wide range of colours are available..

Any drawing area can have a pixmap copied into it - Gtk has comprehensive functions to do that.

However, I should have linked to something more pertinent to your problem, hope this helps:
[URL="http://www.gtkforums.com/viewtopic.php?t=1733&highlight=pixmap"]
http://www.gtkforums.com/viewtopic.php?t=1733&highlight=pixmap[/URL]

Which is based on GtkImage:
[URL="http://library.gnome.org/devel/gtk/stable/GtkImage.html"]
http://library.gnome.org/devel/gtk/stable/GtkImage.html[/URL]

Also note that the pixmaps you create can have pretty much any parameters - resolution, colour depth, etc; they are specified as such so when it comes to the windowing system displaying the content, it can pick up on the parameters and automatically convert to the display device when you present the pixmap to the user.

---

