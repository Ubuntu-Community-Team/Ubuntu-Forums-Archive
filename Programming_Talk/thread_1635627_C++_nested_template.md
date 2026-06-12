---
title: "C++ nested template"
date: 2010-12-02
forum: Programming Talk
---

### Post by JakeFrederix on 2010-12-02
I have a class named red_black_tree, and I wanted to make a map with it.
To do so, I created a class map_entry and map (both defined in map.h, and implemented in map.cpp).

The idea is that a map<T,E> should make a red_black_tree<map_entry<T,E> >.
For some reason, it fails.

When I compile it, the constructor of map fails. Specifically on the line
backend = new red_black_tree<map_entry<T, E> >();

ps: I've included the entire project I'm working on. It comprises several other collection types, aswell as graph, math and string algorithms. So don't be fooled by the size.

The questions are related to the files
red_black_tree.h
red_black_tree.cpp
map.h
map.cpp

---

### Post by C0derBear on 2010-12-02
I don't have my 'buntu handy to test this (at work) but gcc 3.4.4 on Cygwin compiles both map.cpp and red_black_tree.cpp without qualm ( g++ -c -o file.o map.cpp ).

Could you post the error output?

---

### Post by worksofcraft on 2010-12-02
Yeah it compiled OK on my computer too but just fails at the linking stage:

```

$> g++ red_black_tree.cpp map.cpp
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status

```

I didn't get round to working out what was needed.

---

### Post by C0derBear on 2010-12-02
> **worksofcraft said:**
> Yeah it compiled OK on my computer too but just fails at the linking stage:

```

$> g++ red_black_tree.cpp map.cpp
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status

```I didn't get round to working out what was needed.

That's because you have no "main()" function in  the code.

Which, if this is to be a "lib" - seems correct.

---

### Post by JakeFrederix on 2010-12-02
I must confess, I don't work with the terminal to compile C++ code.
I'm a loyal fan of NetBeans. It's so easy to rename variables, or to extract an interface from several classes...

I'll have a look at the commands used to compile in NetBeans.

Thanks for the speedy replies,
Jake

---

### Post by JakeFrederix on 2010-12-02
```

/home/jake/NetBeansProjects/liblib/main.cpp:29: undefined reference to `map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::get(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)'

```

Is the error I'm getting

---

### Post by MadCow108 on 2010-12-02
you cannot implement template functions/classes in .cpp files.
They have to be implemented in header files and included in the files needed.

This is required because the compiler does not know in advance what kind of types are needed and thus cannot produce code without the code using the template

---

### Post by JakeFrederix on 2010-12-02
```

#include "map.h"
#include "map.cpp"

int main(int argc, char** argv) {

    map<int,int>* m = new map<int,int>();
  
}

```

When I use abovementioned code as main.cpp, it will produce following error

```

/tmp/ccsjlIVm.o: In function `map<int, int>::map()':
main.cpp:(.text._ZN3mapIiiEC1Ev[map<int, int>::map()]+0x1d): undefined reference to `red_black_tree<map_entry<int, int> >::red_black_tree()'
collect2: ld returned 1 exit status

```

---

### Post by MadCow108 on 2010-12-02
your still missing the implementation of the template class red_black_tree

for a temporary workaround add:
#include "red_black_tree.cpp"

for more error messages ;)
but these should have a different reason than the wrong location for the source.

---

### Post by C0derBear on 2010-12-02
You may want to consider naming your classes to avoid collision with standard library stuff, either through namespace or actual class names, to guarantee you don't collide in any way with standard stuff.

Debugging linker/compiler issues like that with template code is a PITA.

---

### Post by worksofcraft on 2010-12-03
I see you have quite a lot of very interesting looking code there but Madcow is right: You cannot compile the C++ modules with templates in them because for every different template parameter that you use the compiler needs to generate totally different run time code. In this context you should think, of templates as a bit like macros.

Start by moving all the templated code into the header files.

---

