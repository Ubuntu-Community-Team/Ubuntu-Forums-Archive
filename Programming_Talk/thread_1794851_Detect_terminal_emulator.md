---
title: "Detect terminal emulator"
date: 2011-07-01
forum: Programming Talk
---

### Post by Asmodai on 2011-07-01
Hey,

so I have a console application and I'm trying to get it to run an instance of the default terminal emulator, so the user can see the output even when the program is run from within a file manager.
Right now, I have this:

```
const char* args[]={"gnome-terminal","-x",getExeFileName().c_str(),"--nospawn",0};
execvp("gnome-terminal",const_cast<char**>(args));
```This works. Kinda.
The problem is that it creates another terminal window even when already run from the terminal. And of course, it fails completely when trying to run it outside of an X environment.
So is there any way to reliably detect those two situations in order to avoid executing the above code in those cases?

---

### Post by Asmodai on 2011-07-01
I decided to take advantage of the fact that the output is redirected to .xsession-errors when the program is run from the file manager. In the other cases, the file name associated with stdout is /dev/ptsX or /dev/ttyX.

So is the redirection to .xsession-errors standard? Does this file have the same name on other (important) Linux distributions?
Edit: what about /usr/bin/x-terminal-emulator? It points to a wrapper script for the default terminal emulator on Ubuntu, but is this true for other distributions?

Everything works as expected now, but I'm not sure if it will work for Fedora, Arch, OpenSUSE, etc..

---

