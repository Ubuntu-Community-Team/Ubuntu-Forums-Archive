---
title: "Trying to test compile c++ files"
date: 2009-04-05
forum: Packaging and Compiling Programs
---

### Post by tenpoundbear on 2009-04-05
Hey guys,

I've just managed to get Ubuntu installed and working :)

But now I need to be able to compile my c++ code...
At uni I use these commands...
"g++ -o Game.out <some files here like GL_routines.cpp GL_routines.h main.cpp> -lglut" but when I try this at home I get an error like...

"g++ can found in the following packages:
* g++
* pentium-builder
Try: sudo apt -get install <selected package>
bash: g++: command not found"

What does this mean? And more importantly what do I need to get it resolved?

Any help is appreciated guys... this is so much work to get linux installed and now this ><

---

### Post by vandorjw on 2009-04-05
```
sudo apt-get install build-essential
```

this will install the c++ compiler I believe, along side a bunch of others.

---

### Post by tenpoundbear on 2009-04-05
when I tried that...
I got these errors...

"Reading package lists... done
Building dependency tree.. done
Reading state information.. done
E: Couldn't find package build-essential"

I don't think it is installed yet...
Hmmm... where should I get the package from?

---

### Post by vandorjw on 2009-04-06
are you sure you typed it correctly. When I run that command I get.

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libddccontrol0 ddccontrol-db
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


and yes...I should run autoremove.

---

