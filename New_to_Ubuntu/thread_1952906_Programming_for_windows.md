---
title: "Programming for windows"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by voodoochild850 on 2012-04-05
As part of my job I need to be able to program for windows, I only have Ubuntu 11.10 on my laptop now, so for Linux what C++ IDE's are available and how can I test the programs?

---

### Post by raja.genupula on 2012-04-05
we have many good IDE 
Code Blocks
Geany
Eclipse
Netbeans 

there is a useful discussion for in the IDE's of C++
[http://stackoverflow.com/questions/79210/best-c-ide-for-nix](http://stackoverflow.com/questions/79210/best-c-ide-for-nix)

hope that helps.

---

### Post by santosh83 on 2012-04-05
> **voodoochild850 said:**
> As part of my job I need to be able to program for windows, I only have Ubuntu 11.10 on my laptop now, so for Linux what C++ IDE's are available and how can I test the programs?

Even if you write your Windows code on Linux IDEs, you'd need to cross-compile. That's a messy situation. Even if you do so, you'd still need Windows for testing, or you'd have to test under WINE.

Your best solution is to install Windows (and its development tools) alongside Linux and dual boot **or** install Windows in a virtual machine under Linux.

Back when I used Windows, for my hobbyist programming, Visual C++ Express Edition was good enough. Under Linux I prefer Vim and command-line to compile. But some very good Linux IDEs are Eclipse, Netbeans, KDevelop, and Anjuta.

---

### Post by Mark Phelps on 2012-04-05
> **voodoochild850 said:**
> As part of my job I need to be able to program for windows, ...

Then, you'll need to use MS Windows for testing, if not for actual development. Wine is not going to cut it because, after all, it is NOT a Windows Emulator.

---

### Post by voodoochild850 on 2012-04-05
I was afraid of that, im trying to install codeblocks but I cant get it to install for some reason, but I guess it doesnt really matter anyways

---

