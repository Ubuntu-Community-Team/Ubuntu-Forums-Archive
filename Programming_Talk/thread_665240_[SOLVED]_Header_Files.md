---
title: "[SOLVED] Header Files"
date: 2008-01-12
forum: Programming Talk
---

### Post by Shay el Diyos on 2008-01-12
i've only just started using ubuntu and i wanted to start writing programs so i did the sudo aptitude install build-essential thing.
Now i do have header files but not all....i don't have iostream.h,conio.h and most of the ones i use

i went through the forums and tried this:
sudo aptitude install libc6-dev
and still nothing......it just made my eyes water :)

from what i've got...i can only make 'hello,world' sort of programs.
feels like prison in a way..
it'd be great if someone could help.....thanx in advance

---

### Post by Compyx on 2008-01-12
conio.h is a DOS/Windows header file, so you won't find that on a Linux box. And #include <iostream.h> is deprecated, use #include <iostream> instead.

edit: are you trying to write C programs or C++ programs? If you're writing C programs, you can't use iostream, that's C++. For standard I/O operations with C you need to #include <stdio.h>. And if you really have to do things like clearing the screen, waiting for a key-press and so on, look into ncurses.

---

### Post by Shay el Diyos on 2008-01-12
i just got what you meant......thanx

by the way....is everyone here really old ?
by my calculations you have to have atleast 20 years experience in everything to know stuff like this!!!

---

### Post by Compyx on 2008-01-13
> **Shay el Diyos said:**
> 
by the way....is everyone here really old ?
by my calculations you have to have atleast 20 years experience in everything to know stuff like this!!!

Hehe, no, I'm only 33 years old. But I'm a fanatic who started programming at the age of 7, and I do it for a living and as my main hobby. ;)

---

### Post by LaRoza on 2008-01-13
Read the stickies, especially if you are new to programming in Linux (that is a hint).

See my wiki, if you want references for various languages.

I am 19 and have studied the languages on my wiki, not all equally learned though, and have learned a few that I don't put on the wiki. It takes a long time to master programming (see the link in my sig, and read the article about how to be a programmer in 10 years), but it doesn't take long to learn a language.

---

### Post by Shay el Diyos on 2008-01-20
i'm 20...
@ LaRoza......you make me look old...;P

by the way....i was wondering if you could format a windows partition while it is running.....

---

### Post by Acglaphotis on 2008-01-20
> **Shay el Diyos said:**
> 
by the way....i was wondering if you could format a windows partition while it is running.....

It would be probably a bad idea to try/do.

---

