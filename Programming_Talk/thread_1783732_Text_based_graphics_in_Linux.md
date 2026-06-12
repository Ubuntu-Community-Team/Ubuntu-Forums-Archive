---
title: "Text based graphics in Linux"
date: 2011-06-16
forum: Programming Talk
---

### Post by dagoth_pie on 2011-06-16
Ok so I'm a programming student and my current assignment is to write a text based version of battleship. For the fun of it, I'm wanting to (if I have time) make this cross platform, but I'm in need of a Linux substitute for wincon.h 

Can anyone point me in the direction of some way I can get coloured text in a terminal and print to specific cells in the terminal and that sort of stuff?

---

### Post by Vaphell on 2011-06-16
ncurses library?

---

### Post by amauk on 2011-06-16
Have a look at ncurses
It's a toolkit for CLI apps that allows you to do text based graphics, buttons and other GUI-emulating stuff

A lot of non-trivial CLI apps are written using ncurses, eg. Midnight Commander
[http://en.wikipedia.org/wiki/File:Midnightcommander.png](http://en.wikipedia.org/wiki/File:Midnightcommander.png)

ncurses has also been ported to windows
[http://gnuwin32.sourceforge.net/packages/ncurses.htm](http://gnuwin32.sourceforge.net/packages/ncurses.htm)

---

### Post by dagoth_pie on 2011-06-16
Well that's two votes, I'll be sure to look into it, the only catch is that it has to compile in the markers compiler which is MS VS 2005. I'll be sure to look into it once I've got my game up to what the brief requires. I'm planning to at least make an effort to make my games cross platform, although that may become impossible in the time frame I'll have once I get up to using DirectX. A shame I can't learn game development using OpenGL, but it's my foot in the door to the industry... I hope.

---

### Post by cgroza on 2011-06-16
> **dagoth_pie said:**
> Well that's two votes, I'll be sure to look into it, the only catch is that it has to compile in the markers compiler which is MS VS 2005. I'll be sure to look into it once I've got my game up to what the brief requires. I'm planning to at least make an effort to make my games cross platform, although that may become impossible in the time frame I'll have once I get up to using DirectX. A shame I can't learn game development using OpenGL, but it's my foot in the door to the industry... I hope.
And here is a third vote.

---

