---
title: "kbhit() alternative"
date: 2007-01-10
forum: Programming Talk
---

### Post by yolloms on 2007-01-10
im doin a project in C on ubuntu and was wondering is there an equivalent function to kbhit().

kbhit is contained in conio.h which i dont have and as far as i know is only used on windows.

is there some other similar function i can use r can i actually download and use conio.h and if so where from.

thanks

---

### Post by jblebrun on 2007-01-11
> **yolloms said:**
> im doin a project in C on ubuntu and was wondering is there an equivalent function to kbhit().

kbhit is contained in conio.h which i dont have and as far as i know is only used on windows.

is there some other similar function i can use r can i actually download and use conio.h and if so where from.

thanks

What are you trying to do, exactly?

You might want to check out the ncurses library.

---

### Post by Wim Sturkenboom on 2007-01-11
Assuming that you're trying to create a console application.

Switch your terminal to raw mode; see *man cfmakeraw*. You will now be able to handle single keystrokes.
Use *select* or *poll* to be 'notified' when a keystroke is available.

---

### Post by yolloms on 2007-01-11
> **jblebrun said:**
> What are you trying to do, exactly?

You might want to check out the ncurses library.

i am using the ncurses library.

im tryin to replicate the snake game. the only thing i need to do is make it move continuously. 
i want it to move in the direction entered when a key is pressed and if no key is pressed i want it to move in the same direction until a key is pressed.

---

