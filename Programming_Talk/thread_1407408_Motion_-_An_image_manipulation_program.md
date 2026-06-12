---
title: "Motion - An image manipulation program"
date: 2010-02-15
forum: Programming Talk
---

### Post by rosvall on 2010-02-15
Hello,

I've been developing image manipulation program for some time now. For Windows. Now I'm really considering to start porting it for Linux. It already has a quite nice bunch of effects and filters implemented.

What I'm asking here is that does Linux need another program like this? There is GIMP and some others too already.

I would also need some help to rewrite/port some quite Windows speficic stuff inside Motion's core.

At the moment it's written in C# and large parts with c++. GUI is using Windows forms.

Porting the GUI will be more like a rewrite anyway. So I'm looking which toolkit to use. GTK# would be obvious, but I also started thinking about PyGTK. GUI and all the basic stuff could be written in Python and all the bits that does need some speed could stay in c++. 

So gui would be a rewrite more or less and core library could be ported from existing codebase.

Suggestions about toolkits,programming languages are more than welcome!

Why?

Well first of all: For fun. Other reason are that I just want to start using Linux full time. I used to, but various projects and so on kept me developing stuff for Windows. Not anymore.

License: GPL v3 or MIT.

Nothing is released yet, not even the Windows version. Is there interested people to start a nice community around this kind of project? How about making the best image manipulation program for Linux? ;D

Cheers,
Niko

---

### Post by rosvall on 2010-02-15
An oh I did already create an irc channel for discussion. Feel free to join #motion@IRCnet

Niko

---

