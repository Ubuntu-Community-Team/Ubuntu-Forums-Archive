---
title: "Need an absolutely basic and trivial graphics library for C++, ubuntu"
date: 2009-01-15
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-15
I want to learn how to program very simple graphics (for what I'm doing right now, all I need is to be able to draw dots at particular points and lines between them) in C++ in ubuntu, and have never done any graphics programming of any kind before.  What I would like is a simple graphics library with which I can draw things in a box from a console program, together with an online resource that will provide simple instructions for using it (in particular for using it for simply drawing lines with particular slopes between points and arranging the points nicely in a graph).

The particular project I'm working on is a simple grapher (no fancy trendlines or other such whirlygigs necessary).  It would also be useful (since I don't have much time) if someone could suggest a way that I could simply export data into some file for some grapher or spreadsheet to read (along with information on the format I need to put it in), since I have a project I'm doing and don't have much time left, and don't want to manually input obscene amounts of data into a spreadsheet from a console.  Even if I don't finish it in time though, I *do* want to program the grapher as an exercise.

Thanks!

---

### Post by jimi_hendrix on 2009-01-15
SDL might help

---

### Post by pansz on 2009-01-15
Qt is the best lib suits your need, and there's a very wonderful tutorial for programming a simple game (include drawing lines and dots)

you can install qt toolkit by:
sudo apt-get install qt4-* 

You can choose to use Python or C++ to do your job. if you choose python you will need to install pyqt , you can use 
aptitude search sth...
aptitude show sth...
to find anything you want.

---

### Post by techmarks on 2009-01-16
[PNGwriter]("http://pngwriter.sourceforge.net/") is extremely easy and simple to use, and I'm sure you could create a grapher with it, (I'm assuming this is a 2-d project).
Also [Cairo]("http://www.cairographics.org") is very easy to use.

Cairo is the more flexible and powerful one, but both are very easy to use.

You'll still need to figure out the geometry yourself, but for a 2-d grapher is should not be difficult.

---

### Post by mike_g on 2009-01-16
If you want to produce a graph simply without worrying about the implementation details, and you dont mind using python, you could use [vpython](http://vpython.org/webdoc/index.html). With it you can knock up graphs in about 5 lines of code.

If you want more control SDL with SDLGFX might be a good choice to start. Never used cairo myself, so I cant compare that.

---

### Post by Jonas thomas on 2009-01-16
> **Zorgoth said:**
> I want to learn how to program very simple graphics (for what I'm doing right now, all I need is to be able to draw dots at particular points and lines between them) in C++ in ubuntu, and have never done any graphics programming of any kind before.  What I would like is a simple graphics library with which I can draw things in a box from a console program, together with an online resource that will provide simple instructions for using it (in particular for using it for simply drawing lines with particular slopes between points and arranging the points nicely in a graph).

The particular project I'm working on is a simple grapher (no fancy trendlines or other such whirlygigs necessary).  It would also be useful (since I don't have much time) if someone could suggest a way that I could simply export data into some file for some grapher or spreadsheet to read (along with information on the format I need to put it in), since I have a project I'm doing and don't have much time left, and don't want to manually input obscene amounts of data into a spreadsheet from a console.  Even if I don't finish it in time though, I *do* want to program the grapher as an exercise.

Thanks!

I've been studying a wxwidget tutorial from the [zetcode ]("http://www.zetcode.com/")website. (Although the recent of QT going LGPL has me rethinking that strategy)
I noticed that that are multiple languages represented on this website.  You can poke are around the tutorial and find the language that works for you.

---

### Post by crazyfuturamanoob on 2009-01-16
Maybe use OpenGL + GLUT? Extremely simple, and very powerful graphics library.

---

### Post by bruce89 on 2009-01-16
<ignore me>

---

### Post by wmcbrine on 2009-01-16
> **bruce89 said:**
> i'm surprised no-one's mentioned cairo(mm).#4

---

### Post by Zorgoth on 2009-01-17
I've finished my grapher in QT and it's working quite nicely, thanks!  I will lok into these other libraries too and see which one I prefer.

---

