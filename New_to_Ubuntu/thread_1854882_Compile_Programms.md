---
title: "Compile Programms"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by dep0 on 2011-10-05
Hi, i am new to ubuntu ( i have 11.04 installed ) and i have to write code using C++ for my studies, but as a newbie i don't know where to write code, how to compile it and how to run the programm.
Any help is useful! 
Thanks in advance!

---

### Post by Lars Noodén on 2011-10-05
Use Geany or Kate to write your code, since they are simplest to use.  You can move to fancier IDEs once you know your way around.  

To get started, you'll need the package [g++](http://packages.ubuntu.com/natty/g++)

```
g++ -o test test.cpp
./test
```

---

### Post by hayden92 on 2011-10-05
Simply use the program Gedit that comes standard with Ubuntu to write your code. Once you want to compile your code, open up a terminal, navigate to the source file location and type "g++ <filename>".

To run the newly created binary (it will appear in the same folder) type "./<binaryname>" into the terminal.

Good luck and have fun. Let me know if you need further help!

Hayden

---

### Post by seawolf167 on 2011-10-05
+1 for Geany, then follow Lars Noodén's post above. 

Alternatively you can Google search for something like "c++ hello world ubuntu" and find a ton of how-tos.

---

### Post by dep0 on 2011-10-05
All the suggestions work fine! 
Thanks a lot for the help. 
I'l let you know if i need anything else.

---

### Post by seawolf167 on 2011-10-05
Glad it worked - please mark this thread as Solved under Thread Tools, then open a new thread for any other questions/issues you may run into. Also note that there is a dedicated [programming subforum ]("http://ubuntuforums.org/forumdisplay.php?f=39")too.

---

