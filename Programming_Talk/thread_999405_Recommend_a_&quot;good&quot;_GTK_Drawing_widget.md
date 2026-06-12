---
title: "Recommend a &quot;good&quot; GTK Drawing widget?"
date: 2008-12-01
forum: Programming Talk
---

### Post by Flecko on 2008-12-01
Hello linux programmers,

Before anyone asks, I have read the FAQ for this forum, and have already done extensive searching to see if anyone has solved this problem before, and I haven't found a solution. I've come close, but I need some help.

I'm developing a 2D, tile-based, level editor in C/GTK+ for a game I've already written. I was planning on just editing my XML level files by hand, but that turned out to be an exercise in tedium.

So here's my problem. I've gotten the GUI up and running, and my level loading/saving code is working great, but I haven't found a good widget to use to draw the actual map. I initially tried to use a gtk table that contained gtk images to draw all the tiles. This worked great until I realized that I wouldn't be able to display multi-layered 2D maps. You see, my 2D maps have multiple layers for parallax scrolling. Its tricky to edit the other layers, not knowing where the layer above or below it is.

So this led me on a search for a nice drawing widget that would let me do what I wanted without too much fuss. I've looked at Clutter(the GTK Clutter widget at least) as well as GtkGLExt. They're both overkill for what I need to do.

I also found a few posts floating around the internet about a GTK SDL widget, but that turned out to not be a working solution either.

So does anyone have any suggestions for a widget that I might use to draw a 2D scene with some transparency?

Please let me know...and thankyou in advance.
-Flecko

---

### Post by ZuLuuuuuu on 2008-12-02
Maybe GtkDrawingArea might be a solution for you:

[http://library.gnome.org/devel/gtk/stable/GtkDrawingArea.html](http://library.gnome.org/devel/gtk/stable/GtkDrawingArea.html)

You can draw things on it via Cairo. And AFAIK, Cairo can draw bitmap graphics, as well. This tutorial shows how to draw a clock on it:

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html)

It is in C++ though. But if a clock can be drawed than a level might also be.

---

### Post by mmix on 2008-12-02
[gdkpixbufs]("http://library.gnome.org/devel/gdk/stable/gdk-Pixbufs.html") and [gdkpixmap]("http://library.gnome.org/devel/gdk/stable/gdk-Bitmaps-and-Pixmaps.html#GdkPixmap")


HTH

---

### Post by MicahCarrick on 2008-12-02
Honestly, my fist reaction would be SDL as well, since a 2D game is likely to be developed in SDL right?

But if it's just the level editor, I would probably work with standard GTK and GDK--as mentioned, a GdkPixbuf and GdkPixmap may all you need. Once you've layered your tiles onto a GdkPixmap you can then draw it onto something like a GtkDrawable or another widget.

---

### Post by crazyfuturamanoob on 2008-12-02
I wrote a VERY simple map editor for my 2D soldat clone in python, in haste.
[SIZE="1"](here's a small map I drew with it: [http://www.youtube.com/watch?v=HwzoFSg9C0U](http://www.youtube.com/watch?v=HwzoFSg9C0U))[/SIZE]
I'm not sure if that game will ever be anything, or if I make it public.

The editor sucks, has very little features, some bugs, messy coding and lack of comments.


That's why I'm planning on making a better map editor, and really concentrating on it.

The game engine uses SDL & OpenGL, and I'm planning on making the editor GUI with GTK, so I need a gtk drawing canvas to render the map on.


I found a tutorial about it, but comments are in spain(?) or some other weird language, so it doesn't help much.

That tutorial uses GtkDrawingArea too, with OpenGL. Perhaps there is a better tutorial in english?


Thanks.

---

### Post by Flecko on 2008-12-02
Gentlemen,

Thankyou for the quick responses. 

I looked over gdkpixbufs and gdkpixmaps when I read through Foundations of GTK Development(great book btw if anyone here hasn't read it) and tried a couple of implementations, but didn't see a way to make it work for my map editor. But I'm going to give it a second look. Maybe I missed something.

As for Cairo, I think thats overkill as well for what I'm doing, I just need a nice 2D drawing area. Nothing flashy, just 2D and transparency, I'm not even worried about drawing speed.

As for my game, yes, its written in C/SDL. Like I said before, its a complete engine with only a partially complete game written for it. All I need to do is finish some of the levels and record some sound effects, and it'll be a finished game.

You can check out the src here if you like: [http://www.bensdrivel.com/?page_id=66](http://www.bensdrivel.com/?page_id=66)

(I take no responsibility for the shape that the source code is in, as it has been restructured since I posted it there.)

And I'll be sure and post back with my results.
Also, if anyone has further suggestions, let me know.

Thanks guys!
-Flecko

---

### Post by ZuLuuuuuu on 2008-12-02
> **Flecko said:**
> ...I read through Foundations of GTK Development(great book btw if anyone here hasn't read it)...


I agree, a fantastic book. Actually, I will post regarding with this at gtkforums.com when I have time as the author of the book hangs out there. Encouragement is good for this kind of efforts.

> **Flecko said:**
> And I'll be sure and post back with my results.

Don't forget to post the link to the editor here once it is finished, I love making levels to games :D I couldn't run the game though, it crashed, unfortunately (WinXP)...

---

### Post by Flecko on 2008-12-02
ZuLuuuuuu: Make sure you put the included windows binary in the /src folder, and that you have SDL, SDL_Image, and SDL_gfx installed, as it relies on those DLLs in windows.

I didn't post it with a proper  project file at the time because the laptop I did the windows development on died on me. So I was left with the executable and source. It should compile fine with dev-cpp if you want to try yourself though.

Thanks again,
-Flecko

---

### Post by bruce89 on 2008-12-02
> **ZuLuuuuuu said:**
> This tutorial shows how to draw a clock on it:

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-drawing-clock-example.html)

It is in C++ though. But if a clock can be drawed than a level might also be.

See Writing a Widget with Cairo and GTK+ 2.8, [part 1]("http://gnomejournal.org/article/34/writing-a-widget-using-cairo-and-gtk28") and [part 2]("http://gnomejournal.org/article/36/writing-a-widget-using-cairo-and-gtk28-part-2").

---

