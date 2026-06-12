---
title: "Terminal Graphics"
date: 2009-09-02
forum: Programming Talk
---

### Post by H4F on 2009-09-02
Hi all.
I need just basic graphics in terminal like draw line . color etc. for my university project.
In turbo c++ its done by using BGI library.

how can i use BGI library . or an alternative one to draw line and graphs .

---

### Post by napsy on 2009-09-02
try with ncurses.

---

### Post by Whiffle on 2009-09-02
I don't think you'll have any luck, BGI is windows only and not portable.

---

### Post by wmcbrine on 2009-09-02
BGI is *DOS*. Heck, it's not even that -- it uses the BIOS. (I think BGI stands for BIOS Graphics Interface.) And it doesn't operate in a terminal, except via emulation.

ncurses is no help here, either.

The fact is, you're going to have to learn some GUI or other. SDL is probably the simplest way to get some graphics on screen, and it's not really GUI, but it doesn't do graphics primitives like lines and circles well. So you're probably looking at something like Tk or Gtk. Anyway, whatever you use, it won't be "terminal graphics", and you won't be able to just copy over your antique BGI code, sorry.

Or you could just keep running Turbo C++, under DOSBox.

---

### Post by Whiffle on 2009-09-02
Actually BGI stands for Borland Graphics Interface.

I'm using ncurses right now on a project, and you definitly don't want to draw with it.

---

### Post by H4F on 2009-09-02
Can you please show me an example with drawing lines shapes or anythink else please;

Where do I find API reference for ncurses ?

---

### Post by wmcbrine on 2009-09-02
> **Whiffle said:**
> Actually BGI stands for Borland Graphics Interface.Doh! Of course.

[http://en.wikipedia.org/wiki/Borland_Graphics_Interface](http://en.wikipedia.org/wiki/Borland_Graphics_Interface)

Hey, check out the last link in that article -- "[BOSS Library](http://www.codedread.com/boss.php) - A re-implementation of Borland's Graphics Library (BGI) over SDL". Maybe that's what the OP needs.

---

