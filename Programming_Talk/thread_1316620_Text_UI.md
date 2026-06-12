---
title: "Text UI"
date: 2009-11-06
forum: Programming Talk
---

### Post by leg on 2009-11-06
I want to write a simple game of hangman as a console program and need some advice as to managing the console screen. I have done this kind of task in languages like Pascal and was expecting to find a nice and easy gotoxy() type of function. It seems not and I don't really want to use a seperate library to do this. What strategies can I use to manage the screen? Should I maintain 80x25 array of chars for a screen or is their a better way.

---

### Post by nvteighen on 2009-11-06
> **leg said:**
> I want to write a simple game of hangman as a console program and need some advice as to managing the console screen. I have done this kind of task in languages like Pascal and was expecting to find a nice and easy gotoxy() type of function. It seems not and I don't really want to use a seperate library to do this. What strategies can I use to manage the screen? Should I maintain 80x25 array of chars for a screen or is their a better way.

Screen management is outside the C++ (and C) standard, so you're forced either to implement it yourself or use a library. There is a very widely used library called ncurses, written for C but usable in C++, that allows you to manipulate the terminal.

ncurses is licensed under a very unrestrictive license, even more liberal than a regular 3-clause BSD license, so if your concern about using a library is not to get trapped into GPL's terms, don't worry :) But if your concern is that you don't like to learn new APIs... ;)

---

### Post by leg on 2009-11-06
Thanks I did know about ncurses but my aversion to a 3rd party lib is just that I want to write a simple program that depends on nothing else. So I will have to implement something as simply as possible I suppose. I have been trawling the net for some examples and seen some fairly good ideas. An intersting one from these [very forums]("http://ubuntuforums.org/showthread.php?t=540105").

---

### Post by mmix on 2009-11-06
console development without any library is boring.

IIWY, will try libcaca.

[http://caca.zoy.org/wiki/libcaca](http://caca.zoy.org/wiki/libcaca)

---

