---
title: "Advice in developing C++ program"
date: 2011-11-25
forum: Programming Talk
---

### Post by alexmoca on 2011-11-25
I'm breaking this in a few key steps so it will be easier for everybody to understand my program. Although it might be easier to do it in a different programming language, I really want to do it in C++ so I won't lose my skills completely. I am mostly looking for general advice or opinions on my thoughts. Number 2) is probably the one with which I need most help, but I am open to suggestions of any kind!

Project: I want to develop a program which can retrieve some star brightness measurements (probably [from here]("http://www.planethunters.org/") - highly recommended for astronomy enthusiasts!). [Here]("http://www.planethunters.org/sources/SPH10022763.csv") is a sample .csv file they have on their website (apparently not many stars have data available, but I hope they'll sort this out soon). Based on that data, I want to develop an algorithm which will try to recognize stars which might have planets orbiting them. How do you know when a planet orbits a star? Simply put, when the brightness of the star decreases suddenly and unexplainably for a short period of time, then you have a big clue.

This is how I am thinking to do it:
1) File formatter
I don't like the way that file looks like. Instead of loading their file, skipping line 1, reading line 2, skipping the next 2 lines and then reading the rest of the data, I want to have a script (or maybe I could integrate this functionality in my program using C++) which gets rid of those column names and creates a file which holds just the relevant data. Then all I have to do is just read the whole file without worrying about anything. What do you think? Is it worth the effort? Do I need to think about an alternative?

2) Plotting
I want an interface which is similar to the one on the website (see Screenshot attached). Basically, I want to plot the data somewhere in my window and allow the user to zoom in/out, shrink or increase the time interval (scale the X and Y axes), mark the regions of the plot where they think a planet might have transited and that's pretty much it at the moment. Now this is one major issue: what library should I use? I saw some recommendations so far, but probably someone can suggest one which fits my needs best. And, most importantly, what library would feet my requirements best? Or you think I should choose any of them, integrate the image in my program and from then start to think how to manipulate that image?

3) GUI
God, I am always struggling with this when developing a program. I will probably choose Qt since I used it a little bit a while ago and it seemed quite nice. I am open to suggestions here.

4) Algorithm for detecting planet transits
Although I prefer trying to work myself to exhaustion thinking about it, if you know in which direction I should look, I would be glad to give it a try!

Thanks for your time guys! :)

---

### Post by MG&amp;TL on 2011-11-25
Well, break it up for a start. Nobody likes coding on a single thousand-line file.

Use a revision control system from #1. This will save time later and can be useful if you need to rollback at any point.

Think about what system you're targeting (in this case Debian/Ubuntu) and make sure that the system fits the program.

Just general tips, sorry. :)

---

### Post by alexmoca on 2011-11-25
> **MG&TL said:**
> Well, break it up for a start. Nobody likes coding on a single thousand-line file.

Use a revision control system from #1. This will save time later and can be useful if you need to rollback at any point.

Think about what system you're targeting (in this case Debian/Ubuntu) and make sure that the system fits the program.

Just general tips, sorry. :)

Thanks for your reply, MG&TL! :D I'll definitely not end up with a massive one-file program haha. As for RCS, I think I'll stick to Mercurial, I've been using it for quite a while and we're good friends. :)

---

### Post by MG&amp;TL on 2011-11-25
Also consider using git (what debian uses) or bzr (what ubuntu uses), perhaps two different repositories.

Also, if you're going to make a big app, see if you can make both a Gtk and Qt version-this will look a lot better for only a little effort.

---

### Post by dagoth_pie on 2011-11-27
In regards to the Gui, for an interface like what I think you're after, I'd probably just use minimal GUI tools, widgets, etc. And opt for a bitmap background, with sprites rendered according to positioning. You could easily enough give all of the points plotted in an overall size, then when you wanted to zoom in, scroll around, etc you would have a formula or a matrix to run each of the points through to find their position on the current screen. Sorry if that didn't make much sense.

More specifically, use a large background image, then go for more of a sprite based method of drawing things to the screen, that would be my best recommendation I think, without overcomplicating things, (Personally I'd blow peoples minds by turning a 2D problem into a 3D problem, just because it allows for hardware acceleration) so I'm not the best person to give simple advice. :D

---

### Post by alexmoca on 2012-01-07
Thanks for the help lads! I got started on it and I took the following decisions:

1) The files need to be formatted beforehand. I saw the format of the data is inconsistent, there are extra headers and empty lines in the file.

2) GUI - Qt. Some plotting libraries work are developed with Qt themselves so they should integrate well :)

I do have an issue reading all that data from the file, I will open a separate thread for it.

---

### Post by xytron on 2012-01-07
Having used GTK+, FLTK and Wxwidgets I like FLTK the best.
FLTK is simple.  I've taken FLTK programs from Linux (G++ compiler) and compiled them on Windows 7 with VC++ with only the most trivial changes everything works.  FLTK itself is a small library and can even be compiled statically.  The resulting executables don't get all bloated like with Wxwidgets.

Plus FLTK is well integrated with OpenGL, so it would be easy to plot your time series with it, Cairo is another option.

Just a suggestion. I can't compare it with QT since I've not used it much yet, but QT is a much larger library.

You also should consider that in the future you might wish to integrate your program with a database (such as MySQL or PostgreSQL).  If you are using large amounts of data QT could be better on that front I'm not informed about that.

---

