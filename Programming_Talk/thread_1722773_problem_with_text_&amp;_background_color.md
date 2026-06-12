---
title: "problem with text &amp; background color"
date: 2011-04-06
forum: Programming Talk
---

### Post by med linux on 2011-04-06
hi friends ;

my problem is :

I use the C language and execute my programme in the TERMINAL of ubuntu 

my compiler cc 

NOW I want to make my text colour black and the background colour white 

how to that ?:(

---

### Post by Tony Flury on 2011-04-06
Your best best is to investigate the ncurses libarary and use that to control your terminal output.

Standard C has no facility to change the colourings of the text etc without using a library such as ncurses.

---

### Post by med linux on 2011-04-06
So  "ncurses.h" library like "stdio.h"
but it help me to use colours ?

---

### Post by Tony Flury on 2011-04-07
It provides you with an interface that you need to use which can do all sorts of things - including use colours.

Search for ncurses in Google to find a description and tutorial of how to use the library.

I think I am right in saying that ALL of your output will need to go through the ncurses libary (i.e. you wont be able to use simple printf anymore) - but i might be wrong.

---

