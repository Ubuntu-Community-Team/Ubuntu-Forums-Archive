---
title: "GTK+ G_CALLBACK(function) - Using a class function as the function parameter"
date: 2009-05-31
forum: Programming Talk
---

### Post by PaulM1985 on 2009-05-31
Hi

I keep getting a compiler error:

Window.cpp: In constructor ‘Window::Window(int, char**)’:
Window.cpp:103: error: invalid use of member (did you forget the ‘&’ ?)

I am using 
```

  g_signal_connect(z_button_down, "clicked", 
		   G_CALLBACK(decrease_z), drawing_area);

```

where z_button_down is a button and decrease_z is a member function of the Window class.

Is it possible to use class member functions as parameters, if so how do I go about it?

(Also, if I do put in the '&' as mentioned in the error, I get..

Window.cpp: In constructor ‘Window::Window(int, char**)’:
Window.cpp:103: error: ISO C++ forbids taking the address of an unqualified or bracketed non-static member function to form a pointer to member function.  Say ‘&Window::decrease_z’
Window.cpp:103: error: converting from ‘void (Window::*)(GtkWidget*, void*)’ to ‘void (*)()’
)

Any info would be much appreciated.

Thanks

Paul

---

### Post by SledgeHammer_999 on 2009-05-31
Why are you using GTK+ with C++? Haven't you heard of [www.gtkmm.org](www.gtkmm.org)?(C++ bindings for gtk).


If you insist using it the way you are then the solution is this:
decrease_z must be a static protected method of the Window class.

But I highly recommend you to use gtkmm.

---

### Post by PaulM1985 on 2009-05-31
That is what I need.  I didn't know it existed.  I am trying to transfer from Java to C++.  Is there a package I can use to install this, ie: 

sudo apt-get install [some package]

Paul

---

### Post by SledgeHammer_999 on 2009-05-31
"System->Administration->Synaptic package manager" and search for the programms you want. It's a GUI for apt-get.

Now for the cmd:
```
sudo apt-get install libgtkmm-2.4-dev
```

---

