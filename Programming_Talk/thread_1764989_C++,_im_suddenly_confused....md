---
title: "C++, im suddenly confused..."
date: 2011-05-22
forum: Programming Talk
---

### Post by u-noob-tu on 2011-05-22
so yesterday i used wxwidgets for the first time and made my first GUI (using a tutorial as my base). thing is though, it seemed to have nothing involving C++ in it. i dont know, maybe i just dont have enough experience yet, but i was really thrown off by wxwidgets. i was confused by the lack of anything i have seen before, like "cout" "int main()", and "cin.get()". is that cuz wxwidgets is just the code for the interface and not for the program itself? can someone explain it to me?

---

### Post by simeon87 on 2011-05-22
wxWidgets is for creating a GUI and that's all. You'll need to add more code to make the buttons actually do something. So yes, wxWidgets is just for the graphical interface, not for the program itself.

---

### Post by cgroza on 2011-05-22
wxWidgets is a library. The "int main" is there, but is inserted at compile time by the preprocessor when you use the macro: IMPLEMENT_APP.

Every toolkit has it's learning curve, it is normal.

---

### Post by u-noob-tu on 2011-05-22
So C++ is what makes a program do something, and a toolkit is just visual representation of what it's doing? Wonder how I missed that in my C++ book. That makes a lot more sense now.

---

### Post by unknownPoster on 2011-05-22
> **u-noob-tu said:**
> So C++ is what makes a program do something, and a toolkit is just visual representation of what it's doing? Wonder how I missed that in my C++ book. That makes a lot more sense now.

It's not in your book because that is false.

A GUI toolkit allows your otherwise CLI application to have a Graphical User Interface. 

Appropriate terminal output can be "Visual representation."

---

