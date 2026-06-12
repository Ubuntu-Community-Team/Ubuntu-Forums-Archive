---
title: "Where are C++ Library functions"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by UncleRoy on 2012-01-19
Newbie to Linux methods. Wish to write C++ GUI applications. Installed ECLIPSE, CDT, ANJUTA, GTK. 
Old Windows IDE came with a standard Library. Clicking help gave a function list.
When downloading ANJUTA  GTK was offered as extension. Does CDT (Eclipse extension) have its own Libraries .  How does one get to the function list?

Thanks in advance and also to wildmanne39

---

### Post by CoffeeRain on 2012-01-19
Do you mean the include files? If so, I believe they are in /usr/include.

---

### Post by bouncingwilf on 2012-01-19
Not quite sure what you mean by standard functions/libraries but most valid C++ non-GUI functions obey the C++ standards. With respect to GUI libraries, it depends on what set of libraries you're using QT, gtkmm, wxwidgets etc. If, as your post suggests, your using gtk or the gtkmm functions, then I suggest you install dev-help (sudo apt-get install dev-help) as this appears to be the standard reference documentation to these and associated libraries.

Bouncingwilf

---

### Post by UncleRoy on 2012-01-19
Sorry for the delay I had to sleep. Installed Devhelp which seems good for Docs i didn't even know were there. Thanks for such advice. I chose Anjuta over Eclipse from advice on forums. Will need more time to put it all together. Which Lib is likely to be best?

Also I have related questions :- 

In Windows I would make :-
1) compile All *.cpp (to *.obj presumably Now to *.o) with debug on
2) Lib All (non main) objects into MyLib.lib  (presumably Now to libMy.a ?)
    I then delete all the (non main) objects as part of the make as they are now all in the lib.
3) Link Main.obj with myLib.lib into main.exe (Now main.?)
3) Debug

Does GCC (GDB ?) have a librarian (command line) program?

---

