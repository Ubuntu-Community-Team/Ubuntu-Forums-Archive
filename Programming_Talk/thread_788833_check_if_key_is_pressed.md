---
title: "check if key is pressed"
date: 2008-05-10
forum: Programming Talk
---

### Post by akimatsu123 on 2008-05-10
hi, 

i am writing a C++ program (a game) and i need to check if a key is pressed. what i'm trying to make is an endless loop, in which the program checks if a key is pressed. 

i'm looking for a sort of function that will return 1 if a key is pressed (of course i need to know which one) and 0 if a key is not pressed. it's a sort of typing game where there is a time limit to press a key, so i don want the program to wait for user input (therefore i cant use cin >>)

if anyone also programs in windows, i'm looking for something similar to GetAsyncState().

---

### Post by smartbei on 2008-05-10
[This]("http://forums.fedoraforum.org/archive/index.php/t-147415.html") thread looks helpful.

Also, check out ncurses - I am sure there is a way to do it through there.

---

### Post by samjh on 2008-05-10
> **akimatsu123 said:**
> i am writing a C++ program (a game) and i need to check if a key is pressed. what i'm trying to make is an endless loop, in which the program checks if a key is pressed.

Have you looked at [SDL](www.libsdl.org)?

Take a look at Lessons 8 and 9 of these tutorials:
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

SDL is a library used extensively for games and media applications (including big titles like Quake 4) on Linux, Mac, and Windows.

If you're programming games using C or C++, it's almost a "must know" library.

---

