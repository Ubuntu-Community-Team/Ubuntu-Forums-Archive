---
title: "eclipse C++ error"
date: 2007-05-29
forum: Programming Talk
---

### Post by philbygr on 2007-05-29
i try to write a simple C++ program in eclipse in c++. i have installed CDT plugin. it gives me errors in C++ like it doesn't have the libraries. warning for <iostream> ( i try the <iostream.h> too...) and errors for cout , cin. i think that it undestand only c commands. does anyone know how i add them? in M. visual studio i found that, now it seems me more dificult.... :s 

thanx!

---

### Post by philbygr on 2007-05-29
this is my screenshot, please help!

---

### Post by Blender on 2007-05-29
It would have been better if you just posted the source code instead of a screenshot ;)

Either put the following line after **#include <iostream>**:
```
using namespace std;
```
or prepend all **cout**, **cin**, etc. with **std::**.

---

### Post by philbygr on 2007-05-29
thanx!!! i want to doa  project (in Cpp) for exams... and i' m a little nervus :p

---

### Post by Blender on 2007-05-29
Well, you've got a long way to go.

You'd better buy a C++ book and follow the samples there ;)

---

