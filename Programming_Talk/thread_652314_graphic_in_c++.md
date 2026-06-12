---
title: "graphic in c++"
date: 2007-12-28
forum: Programming Talk
---

### Post by TheLions on 2007-12-28
ok i need  to create a simpe letter guessing game in witch every miss would cause  drawing some part of your body on gibbet.
this is how it should look:

[[IMG]http://img146.imageshack.us/img146/8885/beznaslovavj7.jpg[/IMG]](http://imageshack.us)


where x is your input/output selectable with tab.

how to do that in C (Kdevelop)???

---

### Post by Majorix on 2007-12-28
You have to create a string for each case of the hangman.

---

### Post by TheLions on 2007-12-28
> **Majorix said:**
> You have to create a string for each case of the hangman.

i know that, but i don't know how to create the look on display.
i know to use onla printf for output. H
How to make border, gibbet and all text in border static???

is that something with graphic.h?

---

### Post by Kzin on 2007-12-28
> **TheLions said:**
> i know that, but i don't know how to create the look on display.
i know to use onla printf for output. H
How to make border, gibbet and all text in border static???

is that something with graphic.h?

I would encapsulate all of the rendering code for that bit in one class, or in the case of C a function, and just call it every time a refresh was needed.  Perhaps I don't understand the question, tho.

---

### Post by Fixman on 2007-12-28
Well, I have made a library with some interesting functions. One of them is gotoxy

```
#
int gotoxy(int x, int y) {
#
char essq[100]; // String variable to hold the escape sequence
#
char xstr[100]; // Strings to hold the x and y coordinates
#
char ystr[100]; // Escape sequences must be built with characters
#
 
#
/*
#
** Convert the screen coordinates to strings
#
*/
#
sprintf(xstr, "%d", x);
#
sprintf(ystr, "%d", y);
#
 
#
/*
#
** Build the escape sequence (vertical move)
#
*/
#
essq[0] = '\0';
#
strcat(essq, "\033[");
#
strcat(essq, ystr);
#
 
#
/*
#
** Described in man terminfo as vpa=\E[%p1%dd
#
** Vertical position absolute
#
*/
#
strcat(essq, "d");
#
 
#
/*
#
** Horizontal move
#
** Horizontal position absolute
#
*/
#
strcat(essq, "\033[");
#
strcat(essq, xstr);
#
// Described in man terminfo as hpa=\E[%p1%dG
#
strcat(essq, "G");
#
 
#
/*

** Execute the escape sequence
#
** This will move the cursor to x, y
#
*/
printf("%s", essq);
return 0;
}

```

Then use gotoxy function to go to some place

---

### Post by Kzin on 2007-12-28
cooo fixman

---

### Post by psusi on 2007-12-28
Lookup the (n)curses library.

---

### Post by Fixman on 2007-12-28
> **Kzin said:**
> cooo fixman

Is that "cooooool" or "boooooooo"?

---

### Post by Kzin on 2008-01-03
> **Fixman said:**
> Is that "cooooool" or "boooooooo"?

Hehe, "cooool".  A pretty nifty little bit o code there.

:KS:KS:KS

---

