---
title: "C++ Programming in Ubuntu"
date: 2007-06-30
forum: Programming Talk
---

### Post by Yes on 2007-06-30
I have recently switched from Windows to Ubuntu, and I would like to re-learn C++.  What I need to know is what compiler I should use, and how I make a GUI (Because in Windows, you would just use some of the Windows methods, I believe).

Also, any tutorials concerning OOP programming and GUIs in C++ would be much appreciated.

Thanks.

---

### Post by Smygis on 2007-06-30
install the package build-essential and you get all the compilers you need.

And to make GUI's you first have to choose what widgets you wish to use. 
GTK is most likely what you want. There is also Qt, wxWidgets and many more.

As for IDE (Altho you did not ask ;) ). I like Code::Blocks and geany. But i dont like anjuta.

And on to the main point in this post. Learn Python. Awsome language.

---

### Post by bashologist on 2007-06-30
For C++ Gtk use "Gtkmm", or for Python use "Pygtk". Gtkmm has some really amazing documentation, but it's harder to program with certain things like pointers. For Gtk programming Python might be easier; C++ is more fun tho.

[http://www.gtkmm.org/](http://www.gtkmm.org/)

---

### Post by bclark on 2007-06-30
grab the anjuta ide 'sudo apt-get install anjuta' it's a pretty good c++ ide for smaller projects imho.

Check out: [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")
It's a GREAT reference! Good luck!

---

### Post by Soybean on 2007-07-01
> **Smygis said:**
> install the package build-essential and you get all the compilers you need.
Just a point of clarification: the compiler installed by build-essential is called GCC. The easiest way to use it to compile a single C++ file is by running "g++" from the command line. For example, if your file is called test.cpp, and you want the executable to be called "superawesome", use the following:
```
g++ test.cpp -o superawesome
```

---

### Post by olejorgen on 2007-07-01
You'll probably want to look into **make** too

---

