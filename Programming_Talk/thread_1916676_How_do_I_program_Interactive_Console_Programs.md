---
title: "How do I program Interactive Console Programs?"
date: 2012-01-28
forum: Programming Talk
---

### Post by wiseguy12851 on 2012-01-28
I've seen quite a number of console programs that output different colors, implement paging effects, re-size or fit contents to window area, or even draw ascii menus and buttons that respond to keyboard and mouse events while some even go further with split window allowing either to be scrolled and worked with independently.

It's been nagging at me some time how such dynamic code is implemented in console programs and finally when I do some research, to my surprise, nothing turns up except a few useful links on outputting different colors.

I'd really like to develop dynamic programs like this in C++, can anyone point me in the right direction or answer the above question?

---

### Post by r-senior on 2012-01-28
Sounds like you need ncurses?

[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

---

### Post by sudodus on 2012-01-28
You can use ncurses or the good old ANSI escape sequences, but it will look much nicer to apply ***zenity*** or ***kdialog*** on top of your shellscripts. (I have used kdialog with success a few times.)

[[COLOR="Red"]_http://www.linuxpromagazine.com/Issues/2009/99/Zenity-and-KDialog_[/COLOR]]("http://www.linuxpromagazine.com/Issues/2009/99/Zenity-and-KDialog")

---

### Post by wiseguy12851 on 2012-01-28
I'm only familiar with the std and Qt libraries, what's ncurses, zenity, and kdialog. I can tell kdialog is likely related to kde and as much as I love linux I do want this to be cross-platform. Is ncurses a c++ compatible library or it's own language? I've never heard of ncurses or zenity before.

You also mentioned "Good old fashioned ascii codes" -- I don't recall seeing any ascii codes that implement the level of interactivity I'm wanting nor the lightweight stuff like colors.

---

### Post by sudodus on 2012-01-28
> **wiseguy12851 said:**
> I'm only familiar with the std and Qt libraries, what's ncurses, zenity, and kdialog. I can tell kdialog is likely related to kde and as much as I love linux I do want this to be cross-platform. Is ncurses a c++ compatible library or it's own language? I've never heard of ncurses or zenity before.

You also mentioned "Good old fashioned ascii codes" -- I don't recall seeing any ascii codes that implement the level of interactivity I'm wanting nor the lightweight stuff like colors.
ANSI not ASCII code. I suggest that you browse the internet and read about these methods and tools, look briefly at some tutorials and then decide which method will be best for you.

---

