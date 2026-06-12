---
title: "Programming a game"
date: 2007-09-27
forum: Programming Talk
---

### Post by samona on 2007-09-27
hi,
I have programmed in C++ for school for about 2 years now.  I want to code a chess game but I haven't got the slightest clue how to start.  It doesn't have to even be chess, I just want to create a program with a nice GUI.  

In school all our programs were just source code executed on the console screen.  Getting it to be a program someone can download and install seems like a mystery to me.  Anyone can please help  me?  Thanks in advance.

---

### Post by Wybiral on 2007-09-27
SDL is really good for 2d graphics in C, [http://www.libsdl.org/](http://www.libsdl.org/)

It's in the repositories, btw.

If you want to try a new language, Python + PyGame would be great for something like chess.

---

### Post by samjh on 2007-09-27
I recommend Allegro for creating multi-platform games.
Official site: [http://www.talula.demon.co.uk/allegro/](http://www.talula.demon.co.uk/allegro/)
Community site: [http://www.allegro.cc/](http://www.allegro.cc/)

You can install it using:
```
sudo apt-get install liballegro4.2-dev
```

Here is a very simple quick-start tutorial on C++ and Allegro.  Allegro is actually a C library, by the way.
[http://www.cppgameprogramming.com/cgi/nav.cgi?page=index](http://www.cppgameprogramming.com/cgi/nav.cgi?page=index)
I don't like some of his methods, but it's a good first-time tutorial. :)

---

### Post by slavik on 2007-09-27
also, read about gtk and glade and qt :)

---

### Post by sq377 on 2007-09-27
If you want to get into gui programming, check out gtk.
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

It is alot easier than doing windows gui programming and gets even easier with the c++ wrapper gtkmm but it would be a good idea to understand c interface and know what it is doing.
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)

Once your interfaces start getting complicated, glade can become very helpful.
[http://glade.gnome.org/](http://glade.gnome.org/)

Wybiral was right about sdl.  Make sure to check that out as well.

You can do sdl or opengl on top of gtk as well.
[http://sourceforge.net/projects/gtksdl/](http://sourceforge.net/projects/gtksdl/)
[http://gtkglext.sourceforge.net/](http://gtkglext.sourceforge.net/)

I think all of these libraries should be able to be cross compiled between at least windows and mac as well.

---

### Post by samona on 2007-09-27
Thank you all for the help.  I really appreciate it :)

---

### Post by amo-ej1 on 2007-09-28
Btw, personally I wouldn't advise to start with chess. Chess is a rather complicated game (not that  I play chess ;p) but the algorithms needed to simulate a computer player can be quite dificult.

Next to this, yes in scholar context they always teach you the basics, always stupid console applications, they even never teach you how to use a library of some kind.  So all you need in order to write a GUI applications is make use of an application which offers a GUI framework such as Qt, GTK, wxWidgets, ... or when more graphics/gaming based one would typically use SDL, OpenGL/Glut combo, Allegro etc ...

---

### Post by lisati on 2007-09-28
> **amo-ej1 said:**
> Btw, personally I wouldn't advise to start with chess. Chess is a rather complicated game (not that  I play chess ;p) but the algorithms needed to simulate a computer player can be quite dificult.

Next to this, yes in scholar context they always teach you the basics, always stupid console applications, they even never teach you how to use a library of some kind.  So all you need in order to write a GUI applications is make use of an application which offers a GUI framework such as Qt, GTK, wxWidgets, ... or when more graphics/gaming based one would typically use SDL, OpenGL/Glut combo, Allegro etc ...

Perhaps a version of TicTacToe (a.k.a. noughts and crosses) might be more realistic goal for a beginner than chess. It is also possible to design it in such a way that the game learns as it plays more games, which, if done well, might be an interesting touch for showing off your skills in an educational environment.

---

### Post by dwhitney67 on 2007-09-28
Before you delve into the GUI aspect of any application, game or otherwise, you need to design the application.  And probably the most important part is the "engine" that drives the application.

It seems that a lot of newbs just want to open an editor and start programming.  Thoughts concerning the design must be done first, then the implementation.  Implementers (i.e. programmers) are a dime-a-dozen.  Designers on the other hand are the ones with the real skills.

Btw, one of the first books I ever purchased concerning C++ was "Object-Oriented Programming with C++ and OSF/Motif" by Douglas Young.  The book discusses design issues that are not just relevant to C++, but also to other OO languages, and provides the reader a complete example on how to build a Tic-Tac-Toe GUI application.

---

### Post by Wybiral on 2007-09-28
> **amo-ej1 said:**
> Btw, personally I wouldn't advise to start with chess. Chess is a rather complicated game (not that  I play chess ;p) but the algorithms needed to simulate a computer player can be quite dificult.

Next to this, yes in scholar context they always teach you the basics, always stupid console applications, they even never teach you how to use a library of some kind.  So all you need in order to write a GUI applications is make use of an application which offers a GUI framework such as Qt, GTK, wxWidgets, ... or when more graphics/gaming based one would typically use SDL, OpenGL/Glut combo, Allegro etc ...

He/she doesn't have to make the AI (they never mentioned that anyway).

If all they want is simple movable 2d chess pieces that detect a correct move, I don't think they'll have too big of a problem (especially with something like SDL).

---

### Post by amo-ej1 on 2007-09-28
I agree he didn't mention it, but it's the logical next step :D, writing two player only games suck :D, you can't play it without a second player so it's logical that once you've written it you'd want to take a next step. Which is difficult with chess.  So it would indeed be more realistic to start with something four in a row to tic tac toe'ish which you can perfectly play against the computer.

---

### Post by Wybiral on 2007-09-28
> **amo-ej1 said:**
> I agree he didn't mention it, but it's the logical next step :D, writing two player only games suck :D, you can't play it without a second player so it's logical that once you've written it you'd want to take a next step. Which is difficult with chess.  So it would indeed be more realistic to start with something four in a row to tic tac toe'ish which you can perfectly play against the computer.

Unless they plan to make it a networked game... Or they could look for a pre-existing chess AI project.

---

### Post by Mickeysofine1972 on 2007-09-28
Ahem! (WARNING: blatant plug coming!)

Why not take a look the Ubuntu Game Developers Resource Wiki?

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

It includes all kinds of kewl games programming stuff!

It even has stuf by this guy call Wybiral, (who ever he is :-S) and erm........well.......me XD

Mike

---

### Post by samona on 2007-09-28
hi,
I just spent the last two days trying to install gtk.  It had so many dependencies like cairo, pango, atk, libiconv and much much more.  I downloaded and installed most but now i keep getting errors.  Is there an easier way to install gtk?

---

### Post by scourge on 2007-09-29
> **amo-ej1 said:**
> Btw, personally I wouldn't advise to start with chess. Chess is a rather complicated game (not that  I play chess ;p) but the algorithms needed to simulate a computer player can be quite dificult.

It entirely depends on how strong you want the AI to be. The basics of a chess AI and a tic-tac-toe AI are the same: move generator, minimax search and an evaluation function. I've myself written a grandmaster-level program in C. That took me a whole year, but I'm pretty sure I could write an average human strength program from scratch in a couple of days.

---

