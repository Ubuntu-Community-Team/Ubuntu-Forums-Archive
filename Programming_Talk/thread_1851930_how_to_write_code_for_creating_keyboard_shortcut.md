---
title: "how to write code for creating keyboard shortcut"
date: 2011-09-29
forum: Programming Talk
---

### Post by kemparaju on 2011-09-29
Hi,
 
I am trying to write the code for getting combination of key press as input and executes the corresponding commands.
but my requirement is that, my application should be running in backround, where ever if we press the key, my application should get the input of which key has been pressed. please help me out from this problem.
 
thanks in advance
Kemparaju

---

### Post by narasi on 2011-09-29
This application is being developed for which system?

---

### Post by WasMeHere on 2011-09-29
Do you want to integrate it into an application program, that you develop? In that case you must use the facilities that are available in your programming language.

Or do you want Ubuntu to perform a task, when you enter a key combination? In that case it is quite easy:

Select the menu System -- Settings -- Keyboard Shortcuts

and in the 'Keyboard Shortcuts' window press the 'Add' button for a new action and/or select the (now listed) action and enter or change its shortcut.

---

### Post by kemparaju on 2011-09-30
I am trying to write a program, which will be running at backround and if we press any key, then it will write that key into a file.
for example if we press Alt+k then it will write Alt+k into a file.

---

### Post by WasMeHere on 2011-09-30
> **kemparaju said:**
> I am trying to write a program, which will be running at backround and if we press any key, then it will write that key into a file.
for example if we press Alt+k then it will write Alt+k into a file.
This is actually done by the *keyboard shortcut program* of my previous post. Its command name in terminal is ```
gnome-keybinding-properties
```It is a viewer and editor of a file. Do you want to know the path to that file? Do you want your program to listen all the time, or only when you configure a shortcut?

Remember that linux is open source, so you can get the source code of it and modify it to fit your needs!

Have fun
Olle

---

### Post by karlson on 2011-09-30
> **kemparaju said:**
> I am trying to write a program, which will be running at backround and if we press any key, then it will write that key into a file.
for example if we press Alt+k then it will write Alt+k into a file.

Any reason to write your own keystroke logger?
You can actually start with this:

[http://sourceforge.net/projects/lkl/](http://sourceforge.net/projects/lkl/)

---

### Post by kemparaju on 2011-10-03
Thanks for your valuable reply,
 
I am using "logKeys", for this we have to mention keymap, so how to know which keymap we are using.
 
 
Thanks
Kemparaju

---

