---
title: "Help with compiling and running in g++"
date: 2009-06-05
forum: Programming Talk
---

### Post by Raff1 on 2009-06-05
Hello!

I am new to Ubuntu and trying to figure out how I can compile .cpp-files and run stuff with g++.

I made a simple hello.cpp which cout's "Hello World!". I then compiled it using the terminal

```

#include <iostream>

int main(){

std::cout << "Hello World!";
std::cin.get();

}
```(I later added the cin.get() in order to pause the program in case it would close before I could see the message, but it did not help...)

```

g++ hello.cpp (or: g++ hello.cpp -o something)
```After compiling I find some "a.out" or "something" file, but I dont know what kind of files that is or how I can run them. I have tried double clicking on them and running them from the terminal. Whatever I do, I never spot the intended "Hello World!" message.

So what kind of files do I produce when compiling and how do I use them? How can I see the output? Once I am past this initial barrier I can start playing about with the code it self. :p

Thanks in advance,
Regards Raff1

---

### Post by froggyswamp on 2009-06-05
a.out is the default executable name if you don't specify a custom one through the command line arguments.
To run it just go the folder it is in and type ./a.out + Enter. Should work, if not, sacrifice a goat during full moon and try again.

---

### Post by ibuclaw on 2009-06-05
In the terminal, run
```
./a.out
```
Notice the **./** prefix, that is essential. It is how you run all executable files in your working directory in the terminal.

In Linux, gcc produces [ELF binaries.]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format")

Regards
Iain

---

### Post by MadCow108 on 2009-06-05
a reason you maybe missed the output is because the "endl" for the line break is missing:
std::cout<< "hello" << std::endl;

otherwise it appends the output to the begining of the prompt with no break.

---

### Post by Raff1 on 2009-06-06
> **tinivole said:**
> In the terminal, run
```
./a.out
```Notice the **./** prefix, that is essential. It is how you run all executable files in your working directory in the terminal.

In Linux, gcc produces [ELF binaries.]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format")

Regards
Iain

Ah! Thank you for that very informative post! I understand a bit more about unix executables now. =) It worked like a dream once I knew how to run the file!

[quote=froggyswamp]Should work, if not, sacrifice a goat during full moon and try again.[/quote]My goat is fortunate enough to live yet another day! :p


Regards,
Raff1

---

