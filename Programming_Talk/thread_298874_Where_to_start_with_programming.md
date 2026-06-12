---
title: "Where to start with programming?"
date: 2006-11-13
forum: Programming Talk
---

### Post by clpc on 2006-11-13
Hi all,

I have made the move to Ubuntu from windows and I'm happy with my choice but I do like to write applications.
In Windows I programmed in Delphi 7 and I like the delphi IDE and I am pretty experienced in Pascal.
I have looked at Kylix and Lazarus and as far as I am concerned they are not an option in Ubuntu, way too buggy and problematic.

So I have decided to take the plunge into new terriority and learn something new that integrates well into Ubuntu or Linux in general.

I want to write applications for the Gnome desktop so require an IDE that allows easy form design but also has good support for writing TCP and general Internet applications.

I am getting on a bit now.... the ripe old age of 53 and learning new things seems to take me longer than it ever used to (too much wine, women and rock'n'roll I suppose).

I took a look at [www.java.sun.com](www.java.sun.com) and to be honest after a few hours of looking and downloading and looking even more I was deluding myself to think I even had a slight idea of what the hell it was all about.
Maybe I should just be left out to grass or shot and put out of everyone's agony;)

I have a good understanding of C but this is from the good/bad old days of turboC

So the question is this, "does anyone have any suggestions as to what there is available in the way of programming environments that don't require a degree in computer sciences to use?"

Thanks

---

### Post by Blacktalon on 2006-11-13
Hi

If you are looking for some good IDE's in Linux, I would suggest Eclipse (well for most part, I personally only use it for finding errors and fixing them) or I been told Netbeans is a good one.  These are pretty much the only two I have heard good reviews about.  Though be warned with Eclipse if you are a Ruby or Rails, and or Python, and such programmer, then you will probably need to add some repositories in your Eclipse to work with those (its more so used with java, but I use it for Rails too, with RadRails).


Hope this helps
~BT

---

### Post by Tomosaur on 2006-11-13
Java is a pretty good place to start. C zealots seem to look down on it, and yes, there are things which C is way better at, but Java lets you do pretty cool stuff very quickly. I'd recommend you stick with it, just write some basic hello world stuff if you're having trouble. It took me a while to get used to the syntax.

---

### Post by Antrix on 2006-11-13
I learned programming with Delphi / Pascal myself.

It's all relative to your true understanding of programming, but if it's decent then I would recommend the following for GNOME related programming:

- Any editor with syntax highlighting (I use gedit with the file browser plugin enabled)
- Automake / Autotools
- C++ (speaks for itself) and gdb
- Glade 3 (decent GUI designer, writes to XML file)
- Gtkmm (good C++ wrappers for the Gtk library)
- Libglademm (provides means of accessing the widgets stored in XML files etc.)

It's hard to go wrong with Java, it's a good language. But you would have more fun and better gnome specific results with my suggestions above.

Automake etc may take some time to get used to, but it is definitely worth it. I'm doing my university dissertation with the tools above and I also started with Delphi / Pascal back in the day so thought I'd get my two pennies in.

Edit: Re-reading your original post my suggestion might be tricky and not exactly what you are looking for. Maybe it would be worth looking into Python and its GTK libraries? Not tried it myself but I hear that it is quite easy.

Good luck =)

---

### Post by skymt on 2006-11-13
Here's the development environment I'd suggest for you:

* Language: C#
* Platform: Mono, with Gnome bindings
* IDE: Monodevelop, with integrated GUI form designer

Advantages:

* C# is a very well designed language, and Mono has a very nice standard library.

* Mono applications can integrate very well with the Gnome desktop. In fact, Beagle, Banshee and Tomboy are all written in C#.

* Monodevelop is the only truly integrated IDE for Gnome development. Glade is a very nice GUI designer, but I don't know that it's been integrated into an IDE yet.

* C# is C-like enough to be somewhat familiar, but is also a good introduction to object orientation.

Disadvantages:

* Most C# books focus on the Windows/.NET implementation of C#. The syntax is the same, but there are some differences in the library, IDE, and compiler.

* There have been some patent worries about Mono, due to the fact that the .NET platform and C# language originated at Microsoft.

---

### Post by clpc on 2006-11-13
Well I am certainly glad I got into this community, sensible people with sensible suggestions, thanks very much, your time and effort is appreciated.

I took a quick look at glade and was considering using glade along with a C based language as it means much less to learn.
Java looked like a combined harvester to pick a carrot, maybe I am just not getting it but I installed Java NetBeans and it just looks way to complicated and I like to get into producing stuff a lot quicker at the beginning, I am one of those guys that learns more from my mistakes than I ever do from a book.
So I have plenty to be getting on with now.

Thanks very much and any other ideas or suggestion would be appreciated.

Clive

---

### Post by Lord Illidan on 2006-11-13
I can always shoot you if you want :)

I use Pascal myself on Linux, Turbo Pascal under Dosbox :( for school...ok I don't like it myself either.

Howabout python?

---

### Post by mcglnx on 2006-11-13
Have a look at Python - There is a very simple Tutorial (less than 30 min)

See: [http://www.python.org/](http://www.python.org/) and [http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

---

