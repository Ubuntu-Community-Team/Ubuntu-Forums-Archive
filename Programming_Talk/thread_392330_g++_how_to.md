---
title: "g++ how to"
date: 2007-03-24
forum: Programming Talk
---

### Post by newbie_101 on 2007-03-24
hi all

ive been programing 4 the last 2 week in window. the other day i installed ubuntu on my machine. now i want to do my programing in ubuntu. im using the gEdit and G++ method. but its not like windows...

so far i type in the terminal: 
```
g++ HelloWorld.cpp
```
it created 'a.out'. What do i do now.

thanx,
Newbie_101.

---

### Post by monkeyking on 2007-03-24
To run your program
```
./a.out
```

---

### Post by newbie_101 on 2007-03-24
thank you monky king

---

### Post by monkeyking on 2007-03-24
btw if you want your program to have a more sensible name you can do stuff like.
```

g++ -o smartname HelloWorld.cpp

```

---

### Post by samjh on 2007-03-25
To get an output file:
```
g++ -o outputfile.bin sourcecode.cpp
```

To display all compiler warnings:
```
g++ -Wall -o outputfile.bin sourceode.cpp
```

To generate debugging information (necessary if you wish to use gdb for debugging):
```
g++ -g -o outputfile.bin sourceode.cpp
```

Use -O, -O1, -O2, or -O3 for speed optimisations:
```
g++ -O2 -o outputfile.bin sourcecode.cpp
```

Use -s to strip symbols, which reduces output file size"
```
g++ -s -o outputfile.bin sourcecode.cpp
```

You can combine all that:
```
g++ -s -O2 -Wall -o outputfile.bin sourcecode.cpp
```

For more info: [http://www.die.net/doc/linux/man/man1/g++.1.html](http://www.die.net/doc/linux/man/man1/g++.1.html)

---

### Post by lnostdal on 2007-03-25
Also see [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/) (great for beginners) and of course [http://gcc.gnu.org/onlinedocs/gcc/](http://gcc.gnu.org/onlinedocs/gcc/) (and for the preprocessor: [http://gcc.gnu.org/onlinedocs/cpp/](http://gcc.gnu.org/onlinedocs/cpp/) ).

---

