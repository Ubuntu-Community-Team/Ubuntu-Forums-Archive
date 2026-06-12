---
title: "Java/C/anything - update single line on screen - like a progress bar"
date: 2008-06-19
forum: Programming Talk
---

### Post by Meson on 2008-06-19
In general, how do you write a cli program that updates the same text field in the shell?  Like the progress bars that show download speed...

---

### Post by kknd on 2008-06-19
You can use the library ncurses!

---

### Post by Can+~ on 2008-06-19
Or start writing over the same line with '\r' (at least on unix, dunno if this works on windows).

---

### Post by Meson on 2008-06-24
I've had a lot of fun writing a program using ncurses and compiled/ran it successfully on my system.  I can't seem to find a download of the library for Windows.  Does such a thing exist?

---

### Post by henchman on 2008-06-25
There is a thread regarding this question [here]("http://ubuntuforums.org/showthread.php?t=620308").

If you only want to have this function just #include <conio.h> and use gotoxy(x,y); :)

---

