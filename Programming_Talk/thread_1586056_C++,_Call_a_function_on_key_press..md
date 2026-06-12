---
title: "C++, Call a function on key press."
date: 2010-10-01
forum: Programming Talk
---

### Post by cgroza on 2010-10-01
Hello, I built my address book program and i want to call a function on key press. I want to use this so i the user can navigate back into the program. I searched the internet but still could not figure it out. There is some built in function that listens to a certain keypress?

---

### Post by Simian Man on 2010-10-01
Is this a console application or a GUI one?  There is no functionality for this in standard C++, so it depends on what extra library you want to use.

---

### Post by cgroza on 2010-10-01
It is a console one. If there is no standard way to do it could you suggest a method?

---

### Post by Sub101 on 2010-10-01
> **cgroza said:**
> It is a console one. If there is no standard way to do it could you suggest a method?

Can I clarify; You want to minimize the terminal then go back to it?

Or is it exit the application then return to it?

---

### Post by cgroza on 2010-10-01
> **Sub101 said:**
> Can I clarify; You want to minimize the terminal then go back to it?

Or is it exit the application then return to it?

Ok, the user selects to create an entry but changes its mind, I want to give him the option to go back to the main menu.

---

### Post by Sub101 on 2010-10-01
> **cgroza said:**
> Ok, the user selects to create an entry but changes its mind, I want to give him the option to go back to the main menu.

In that case you could do something like;

On every input option include an IF statement where, if its satisfied the application returns to the menus.

---

### Post by Simian Man on 2010-10-01
I'd recommend using ncurses which is a very powerful library for making nice console applications.

---

### Post by cgroza on 2010-10-01
Hmm, Thank you for your time. I will check ncurses but in the meanwhile i will try an if statement.

---

