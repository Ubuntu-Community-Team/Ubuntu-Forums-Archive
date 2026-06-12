---
title: "Writing GUI programs that are compatible with the Unity desktop."
date: 2011-10-21
forum: Programming Talk
---

### Post by sepoto on 2011-10-21
I have in mind to write a program based of "libusb" which can be found at [http://libusb.org/](http://libusb.org/). I would like my program to have a GUI interface. I have written many GUI programs for Windows in different languages including C++ for Win32 and C#. I would like to stay with the language I know best at this point which is C++ although I am not opposed to learning Python if that would make development faster. Will the GTK+ library be compatible with the Unity desktop? If not is there some library and or language that should take preference in development for Ubuntu 11.1 programs?

Thanks!

---

### Post by cgroza on 2011-10-21
You do not need to do "special" programming to be compatible with Unity, but if you want better integration with the Launcher or the Dash, there is an API for that.

---

### Post by t1497f35 on 2011-10-22
There's no API preference of Python over C or C++, since Python is usually just calling the C API through its bindings.
Gtk is compatible with Unity, but Unity and Ubuntu in general has some APIs that are specific to Ubuntu, like the notification system.
A typical "integrated" Ubuntu application is written in C/C++/Python using Gtk or Qt, sometimes using some specific Ubuntu APIs if the programmer thinks it's worth it. You are not bound to use specific Unity/Ubuntu APIs to make a decent program, unless the logic/design of the program demands so.

---

### Post by Fallen_Demon on 2011-10-23
The beauty of Linux distros is that you can use any graphical library you want. Gtk+ will work just fine, or you can fire up Qt or even OpenGL if you really want to. There really is no limit to what you can use :)

---

