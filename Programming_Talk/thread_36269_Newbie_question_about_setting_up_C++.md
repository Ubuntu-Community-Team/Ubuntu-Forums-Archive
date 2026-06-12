---
title: "Newbie question about setting up C++"
date: 2005-05-22
forum: Programming Talk
---

### Post by veraction on 2005-05-22
Ok, just set up java on my box, now I'm trying for C++.

I made a small test program:

```
#include <iostream>
using namespace std;
int main() {
      cout << "C++ Test!" << endl;
}
``` 

I think I can use the g++ command to create an output file, a.out, however I don't know what to do from there. gcc produces errors...

I'm used to having a script set up so it compiles everything & links it together   :???: 

So, How should I compile this?
Thanks ;)

---

### Post by jerome bettis on 2005-05-22
g++ file.cpp
./a.out

or g++ -o objectfilename file.cpp
./objectfilename

if you just type a.out it will say command not found because the current directory is not in $PATH  .. you could add it to the path or use ./ to  execute a file in the current directory which is represented by .

oh yeah, you'll want to sudo apt-get install build-essential if you haven't already done so

---

### Post by veraction on 2005-05-22
ok, I can use that command to make it work.

but is there any easy way to make a Makefile or something - in case I have 20+ .o files?

---

### Post by toojays on 2005-05-22
The best way to make a Makefile is still to do it by hand. If you take advantage of GNU Make's builtin rules, your project with multiple compilation units can be done with one Makefile rule:```

executable : file1.o file2.o file3.o
```
GNU Make knows how to create file1.o if you have a file1.cpp.

For more information, see the [GNU Make Manual](http://www.gnu.org/software/make/manual/make.html).

---

### Post by LordHunter317 on 2005-05-22
[QUOTE=jerome bettis] you could add it to the path or use ./ to execute a file in the current directory which is represented by .[/quote]**NO!**.  Don't add '.' to PATH unless you know exactly what you're doing.

And if even you do, still don't do it.

---

### Post by mendicant on 2005-05-22
You can even have make (via gcc -M) generate your dependencies for you.  Look here:
[http://make.paulandlesley.org/autodep.html](http://make.paulandlesley.org/autodep.html)
(it's also in the info pages for make).

---

### Post by jerome bettis on 2005-05-22
[QUOTE=LordHunter317]**NO!**.  Don't add '.' to PATH unless you know exactly what you're doing.

And if even you do, still don't do it.[/QUOTE]
 yeah that's right i forgot to mention that.

it's a security issue.  if someone puts an executable in that directory called ls and you type ls like you always do, the one in the current directory is the one that gets ran, and who knows what it could do.

---

