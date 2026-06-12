---
title: "GCC help"
date: 2007-07-01
forum: Programming Talk
---

### Post by Shorty Tubbs on 2007-07-01
whenever i try to compile a C++ script using GCC i get this. 

gcc: error trying to exec 'cc1plus': execvp: No such file or director

im using feisty, and the GCC edition thats pre-loaded. Help?

---

### Post by Modred on 2007-07-02
For C++ files try using g++ instead of gcc.

---

### Post by Shorty Tubbs on 2007-07-02
Ah...genius

it will run the commands, but now theres no output

---

### Post by dsl on 2007-07-02
What is the command you are typing

If you type

g++ myprogram.cpp

then the output will be named

a.out

and you can execute it by typing

./a.out

---

### Post by Modred on 2007-07-02
On that note:

```
g++ -o myprogram myprogram.cpp
```

The "-o myprogram" tells g++ to name your output "myprogram" instead of "a.out".

---

### Post by Shorty Tubbs on 2007-07-02
dsl, that works beautifully. Modred, um, somehow i dont think im supposed to get maybe a hundred or so lines of complaints and error messages

cheers for the help

---

### Post by Modred on 2007-07-02
> **Shorty Tubbs said:**
> Modred, um, somehow i dont think im supposed to get maybe a hundred or so lines of complaints and error messages

Can't say I've ever heard of g++ going beserk because you gave it a different name for the output. o_O

You might move the "-o myprogram" to the end of the line, after typing the source file name, but that hasn't ever changed the result in my experience.  And make sure that's an o, not a 0.

---

### Post by dsl on 2007-07-03
Modred's suggestion must work. "minus lowercase o" with no space in between, then a space, then the name of the executable you like (needs not be similar to the source)

---

### Post by nitro_n2o on 2007-07-03
Just a quick comment do NOT do this: 

g++ myprogram.cpp -o myprogram.cpp 

This might happen when click the tab or something make sure you don't do it so often :)

---

### Post by dsl on 2007-07-04
You can do that just once ;-) then your source code is gone.

---

