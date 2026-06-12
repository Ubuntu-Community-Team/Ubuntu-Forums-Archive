---
title: "Help: Geany"
date: 2010-09-08
forum: Packaging and Compiling Programs
---

### Post by fatalfix on 2010-09-08
good day to all...):P

in windows, im using dev c++
and it works nicely..

in ubuntu, im using geany, but i cant seem to execute my program..
theres an error..about script.hh is missing..

i already fixed the permission denied problem, but i cant fix the execute problem..

the problem is in 
code:27


(sorry for the bad english)


thanks..

---

### Post by fallenshadow on 2010-09-08
Include this sentence: 

```
using namespace std;
``` 

before your main function.

---

