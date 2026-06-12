---
title: "[C++] eclipse, CDT, &quot;g++: no input files &quot;"
date: 2009-01-24
forum: Programming Talk
---

### Post by Asday on 2009-01-24
I've got eclipse 3.2, along with CDT.  I created a...  Standard Make C++ Project (?), wrote some hello world, and tried to...  Run it.  Forgive my terminology.

After piddling about with the settings, to get them as close to sensible as I can think, and it returns "g++: no input files".

Please help, I'm trying so hard to get into C++, and eclipse is just demotivating me.  (Heh, learning the language seems easy compared to getting it to work under eclipse.)

Thanks.

---

### Post by Caduceus on 2009-01-24
I don't use Eclipse so I can't be of too much help but when I get that error with g++ it's usually missing the name of what I want the file to be called (if that makes any sense). For example (with no file name)

```
g++ -o [path to file].cpp
```

I get the error, but with a name:

```
g++ -o **hello** [path to file].cpp
```

It (usually) compiles. Maybe something along those lines?

---

### Post by Asday on 2009-01-25
That does indeed look like the solution to my problem, but I can't find an option for that in Eclipse itself.

---

