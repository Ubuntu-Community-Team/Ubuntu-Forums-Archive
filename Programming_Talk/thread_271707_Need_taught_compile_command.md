---
title: "Need taught compile command"
date: 2006-10-05
forum: Programming Talk
---

### Post by stealth75711 on 2006-10-05
hi,

I installed the build essential and wrote simple
c++ program using text editor when i compile it
there's no pop up terminal window that executes
the program.  My question is how do i execute
the program after i write it?:confused:

// a simple c++ program
#include <iostream>
using namespace std;

int main()
{
	cout << "Programming is ";
	cout << "great fun!";
	
	cin.ignore();
	cin.get();
	
	return 0;
}



then when i try to compile it i get this
error:

           >g++ -pedantic -Os -fno-exceptions -c simple.cpp -o simple.o
>Exit code: 2

---

### Post by Jussi Kukkonen on 2006-10-05
> My question is how do i execute
the program after i write it?
Like any other executables. If you don't specify the executable name in the compile command, it will be *a.out*, so:
```
jku@luna:~$ ./a.out
Programming is great fun!

jku@luna:~$ 
```
And yes, your code compiles and works here...

---

### Post by amo-ej1 on 2006-10-05
Hi, well you compiled your source, but you didn't really link it. 

In 

```

g++ -pedantic -Os -fno-exceptions -c simple.cpp -o simple.o

```

you notice the -c flags and the -o simple.o. This means only compile (not link) the sourcefile and store the result at 'simple.o'

If you replace this by
```

g++ -pedantic -Os -fno-exceptions simple.cpp -o simple

```
It will compile and you can execute it by running "./simple"  from the path where you compiled your application. (you have to add ./ before the name of the application because your current directory isn't probably in your path).

---

### Post by stealth75711 on 2006-10-05
i dont understand yet
i put in console and got 
this message:
amin@ubuntu:~$ g++ -pedantic -Os -fno-exceptions simple.cpp -o simple
g++: simple.cpp: No such file or directory
g++: no input files
amin@ubuntu:~$ ./a.out
bash: ./a.out: No such file or directory
amin@ubuntu:~$ ./simple
bash: ./simple: No such file or directory
amin@ubuntu:~$ ./simple/amin/programs
bash: ./simple/amin/programs: No such file or directory
amin@ubuntu:~$

---

### Post by stealth75711 on 2006-10-05
amin@ubuntu:~$ /home/amin/programs/simple.cpp
bash: /home/amin/programs/simple.cpp: Permission denied


It says this now i am not sure what i am doing wrong:confused: :confused: :confused: :confused:

---

### Post by stealth75711 on 2006-10-05
amin@ubuntu:~$ ./simple
Programming is great fun!amin@ubuntu:~$
amin@ubuntu:~$ ./hello
Hello World!
amin@ubuntu:~$


I finally got it.. Thanks guys
for helping mr figure this out
:KS :KS :KS :KS 

heres 4 stars keep up the good work
well i must be off to become a
programming genius

Hello World!

---

### Post by amo-ej1 on 2006-10-05
it stays amazing to see how much people can learn from their own mistakes ;)

---

