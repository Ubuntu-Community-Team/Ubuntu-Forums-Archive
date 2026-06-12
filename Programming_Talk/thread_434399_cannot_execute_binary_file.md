---
title: "cannot execute binary file"
date: 2007-05-05
forum: Programming Talk
---

### Post by cbrad on 2007-05-05
I created a program in c++
I compiled the program without errors

$ g++ -c filename -o filename.o

$ ./filename.o

message : cannot execute binary file

can anyone help?

thanks

---

### Post by Wybiral on 2007-05-06
The "-c" flag generates an object file... This isn't what you want to execute (object files are used for linking).

Omit the "-c" flag and don't use the ".o" extension if you are creating an executable file.

---

### Post by WW on 2007-05-06
[For example...]("http://ubuntuforums.org/showpost.php?p=2448880&postcount=3")

---

### Post by WW on 2007-05-06
[An example with multple source files...]("http://ubuntuforums.org/showpost.php?p=2524773&postcount=9")

---

