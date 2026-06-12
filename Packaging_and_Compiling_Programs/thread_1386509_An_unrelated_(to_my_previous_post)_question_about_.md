---
title: "An unrelated (to my previous post) question about wxWidgets"
date: 2010-01-20
forum: Packaging and Compiling Programs
---

### Post by scared0o0rabbit on 2010-01-20
So if I want to distribute a small application I wrote that uses wxwidgets, do I need to include any kind of libraries or anything for people to use the binaries?  If so, is it more appropriate to include a text file with instructions of where to get the dependencies or to include the files themselves?

Any guidance would be appreciated as I've never released a binary for Linux before, and I know the Linux (especially Ubuntu) mindset relies more on repositories and the like than windows does.

---

### Post by SevenMachines on 2010-01-21
Its true, source packages are always going to be better for distributions :)
For a small binary i would probably just include instructions on which libraries (and which versions) are needed to be installed. you dont want to start lumping outside libraries in with it unless its immensely critical

---

### Post by scared0o0rabbit on 2010-01-22
That's kind of what I figured.

This may sound weird, but is there a way to figure out which libraries are needed for the executable.  Or should I just tell people they need to install wxwidgets 2.8 to make the application work, since that was what I used to build it?

---

### Post by Yellow Pasque on 2010-01-25
Distribute it in .deb form and depend on libwxgtk2.8-0 package

> This may sound weird, but is there a way to figure out which libraries are needed for the executable.
..
```
ldd *executablefilename*
```

---

