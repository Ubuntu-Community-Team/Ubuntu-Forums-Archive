---
title: "Clearing/Refreshing the screen"
date: 2008-09-03
forum: Programming Talk
---

### Post by lordhaworth on 2008-09-03
Hi all

I have a few programs now, for which Id like to clear (or refresh, however you want to put it) the screen. For example, a pacman - style game Ive written: itd look a lot better if it didnt pan down the console the way it does at the minute + you can see the old movements by scrolling up! 
It would also be nice to use after having selected a menu option etc...

I was wondering if there was a built in method for clearing the screen Fortran 90? - (I dont think this is likely)

Alternatively if there is a generic subroutine I could create from scratch and just add to my various programs an outline of how I might do this would be appreciated. I program in C aswell so could probably interpret a solution in C to Fortran. 


Cheers

Tom

---

### Post by Zugzwang on 2008-09-03
You might want to look into the library ncurses. It allows you to move the cursor to some point on the terminal window, for example, so you can "reuse" space on the terminal. Use google to find out more.

---

### Post by lordhaworth on 2008-09-03
hmmm, i see what you mean - position the curser where the new print will overwrite the old text. It would likely work for the pacman thing but im having visions of new text running into old text beneath it!


ill give it a shot and let you know how it went

---

