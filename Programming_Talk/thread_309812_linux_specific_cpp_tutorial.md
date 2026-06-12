---
title: "linux specific cpp tutorial"
date: 2006-11-30
forum: Programming Talk
---

### Post by falkenberg_cph on 2006-11-30
Hi
I have found a create online tutorial to start off learning c++. Unfortunately allreade the "hello world" is windows specific, with its 
iostream library.
Can anyone guide me to a linux specific tutorial?

/Carsten

---

### Post by daniminas on 2006-11-30
//Begin hello.cpp
#include <iostream>
 
int main(int argc, char** argv)
{
cout << "HELLO WORLD!" << endl;
return 0;
}

> g++ -o hello hello.cpp

> chmod 777 hello

> ./hello
HELLO WORLD!


:))

---

### Post by falkenberg_cph on 2006-11-30
So you can use iostream???
I read another place on the forum, that instead of iostream i should use stdio.h - so i figured, if the simplest program would differ between linux and windows, i better learn linux from the start.

[edit]: I have now found this thread: [http://www.ubuntuforums.org/showthread.php?t=255970&highlight=c%2B%2B+unix](http://www.ubuntuforums.org/showthread.php?t=255970&highlight=c%2B%2B+unix)
Looks promising

---

### Post by falkenberg_cph on 2006-11-30
:-? Saved my file hello.c instead of hello.cpp
Thats why iostream didnt work

](*,)

---

### Post by daniminas on 2006-11-30
I use g++ to compile *.cpp files and gcc to *.c files

---

