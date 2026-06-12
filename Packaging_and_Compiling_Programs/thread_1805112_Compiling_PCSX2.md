---
title: "Compiling PCSX2"
date: 2011-07-15
forum: Packaging and Compiling Programs
---

### Post by sakishrist on 2011-07-15
Hello everyone!

I was trying to compile PCSX2 but encountered a strange phenomenon!!! The problem might be that I have a 64bit system and I have set up a chroot environment. I belive I have downloaded all the dependencies. 

The problem is, the compiler only looks for header files (or paths to be more accurate) in  the "include" directory and not in the subdirectories. An example would be this line:```
#include <gdk/gdk.h>
```Here, the compiler should actually search for that file in "/usr/include/**gtk-2.0**/gtk/gtk.h" but it only looks for it like this:  "/usr/include/gtk/gtk.h". I am sure of this because if I copy the folder from gtk-2.0 to include, then it goes on to the next header.

I used **cmake** to create **CMakeLists.txt** and then I tried with the script they provide, like this: **$ ruby build.rb** and with **make**, but none of it works.

Thanks in advance!!! [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

