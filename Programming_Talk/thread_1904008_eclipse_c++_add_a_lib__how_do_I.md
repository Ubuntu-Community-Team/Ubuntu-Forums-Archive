---
title: "eclipse c++ add a lib ? how do I ?"
date: 2012-01-03
forum: Programming Talk
---

### Post by highspider on 2012-01-03
how do add libs to the complier for eclipse?
and what is process correctly called because I have NO luck searching it.

if I was using the command line it would just be adding -lncurese
```

g++ GAME.cpp -o game [COLOR=DarkGreen]-lncurses[/COLOR]

```Eclipses 
```
**** Build of configuration Debug for project GAME ****
make all 
Building target: GAME
Invoking: GCC C++ Linker
[COLOR=Red]g++  -o"GAME"  ./src/GAME.o [/COLOR]  
./src/GAME.o: In function `main':
[COLOR=Red]/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:17: undefined reference to `initscr'
/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:18: undefined reference to `printw'
/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:19: undefined reference to `refresh'
/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:20: undefined reference to `stdscr'
/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:20: undefined reference to `wgetch'
/home/keegan/cpp/GAME/Debug/../src/GAME.cpp:21: undefined reference to `endwin'[/COLOR]
collect2: ld returned 1 exit status
make: *** [GAME] Error 1

```

---

### Post by highspider on 2012-01-03
found it finally

right click the project file -> select properties
settings->GCC C++ Linker->libraries->add new
ncurses 

which is now the same as -lncures 
i guess the -l stands for library

---

