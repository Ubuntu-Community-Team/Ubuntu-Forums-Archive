---
title: "Reading Text From Terminal Via C++"
date: 2006-06-30
forum: Programming Talk
---

### Post by camRW on 2006-06-30
I've just started programming in Linux and I would like to know how to retrieve text that is written to the terminal via another program.  Does anyone have any links, guides, or advice to accomplish this in C++?

---

### Post by wmcbrine on 2006-06-30
I assume you're looking for something more than "cin >>"?

---

### Post by camRW on 2006-06-30
I guess I didn't explain myself correctly.  I want to code a program that makes a map generated from a text based game.  The game (MUD) writes a description of the area the character is located in the game to the terminal.  I want to be able to capture the description from the terminal and compare to a string and then be able to determine where to place a piece of the map.  I have the rest worked out, I just need a way to retrieve what is written from another program to the terminal.

---

### Post by LordHunter317 on 2006-07-01
I don't see how cin won't accomplish this.  No two programs can really share the TTY at once without agreeing on how to do it in advance, which is generally a risk endevour anyway.

---

### Post by Horsman on 2006-07-01
It sounds like you want to pipe the output of the other program into your program, correct?

so what you will do is read from standard input on your program (aka stdin), and when the program is run (run it froma  shell script), do this:

```
(MUD) | (your app)
```
where MUD is teh game that outputs to stdout and my app is the name of your c++ program.

---

### Post by camRW on 2006-07-01
Thank you Horsman that is exactly what I was looking for (had a bit of trouble explaining it though).

---

### Post by LordHunter317 on 2006-07-01
In your application, you still will use cin, though.  Pipes are a shell function, they're more or less transparent to your application.

---

