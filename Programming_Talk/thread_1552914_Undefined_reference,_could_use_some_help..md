---
title: "Undefined reference, could use some help."
date: 2010-08-14
forum: Programming Talk
---

### Post by DarkAmbient on 2010-08-14
Heya, I just started to program again on an old project of mine.

Last time i coded on (my to be a 2D game using SDL) it worked fine i remember.

I hav'nt been programming in C++ for a long time, only some PHP.. so I'm kinda rusty with C++ as of now.

Anyway, the outputs i get from compiling with ```
g++ -o pagan_test main.cpp -lSDL
```

is

```
main.cpp:(.text+0x16): undefined reference to `CGame::CGame()'
main.cpp:(.text+0x5e): undefined reference to `CGame::initialize(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
main.cpp:(.text+0xc4): undefined reference to `CGame::run()'
main.cpp:(.text+0xd5): undefined reference to `CGame::~CGame()'
main.cpp:(.text+0xf3): undefined reference to `CGame::~CGame()'
collect2: ld returned 1 exit status

```

The main.cpp and game header looks like this.

main.cpp:

```


- wiped clean -


```

game.h

```

- wiped clean -

```

The game header has a cpp file aswell* But dont think i need to print out more than (even if) that?

As I said, I hav'nt been coding in C++ for a while now. 

So please, anyone got a clue? [COLOR="Red"]Could it be my inexperience with compiling in linux that causes this??[/COLOR]
If that's the case then I'll remove this, readup some more and apologize myself :o

---

### Post by MadCow108 on 2010-08-14
you need to compile game.cpp too and link that with the compiled main.cpp:

g++ -o pagan_test main.cpp game.cpp -lSDL

or equivalent:
g++ -o main.o main.cpp -c
g++ -o game.o game.cpp -c
g++ -o pagan_test main.o game.o -lSDL

---

### Post by DarkAmbient on 2010-08-14
thanks for the quick reply, so it turned out to be my inexperience with compiling in linux after all. Last time i spent more time with C++ I was still under windows using Bloodshed.

I got a another question then, do I need to link all of the headers/source files when compiling.. beacause so far I got about 60 sourcefiles. (separating classes into their own h/cpp and im a oop-nazi) :confused:

---

### Post by MadCow108 on 2010-08-14
for larger projects you usually write makefiles for make
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

you might even want to use a build system like autotools or cmake

---

### Post by DarkAmbient on 2010-08-14
> **MadCow108 said:**
> for larger projects you usually write makefiles for make
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

you might even want to use a build system like autotools or cmake

All'right, I'll try to learn more about makefiles. Guess I started in the wrong end trying to figuring out how to compile in linux. thanks a bunch Madcow, you sure enlighted my day. :-)

---

