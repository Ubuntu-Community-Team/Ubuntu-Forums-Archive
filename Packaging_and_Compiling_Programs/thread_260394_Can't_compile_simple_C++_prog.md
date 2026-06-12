---
title: "Can't compile simple C++ prog?"
date: 2006-09-18
forum: Packaging and Compiling Programs
---

### Post by UndergroundHangout on 2006-09-18
greetings,

im trying to learn c++ and was working through a tutorial and it wanted me to make a simple "hello world" program. when i went to compile it gave errors.

```
#include <iostream>

int main()
{
  cout<<"HEY, you, I'm alive!  Oh, and Hello World!";
  return 0;    
}

```

and i got these errors:
```
root@error:/home/mark/Programming# g++ helloworld.cpp
helloworld.cpp: In function ‘int main()’:
helloworld.cpp:5: error: ‘cout’ was not declared in this scope
```
```
root@error:/home/mark/Programming# gcc helloworld.cpp
helloworld.cpp: In function ‘int main()’:
helloworld.cpp:5: error: ‘cout’ was not declared in this scope
```
```
root@error:/home/mark/Programming# bcc helloworld.cpp
ld86: cannot open input file crt0.o
```

i have build-essential installed, also have bcc installed. i cant seem to find any info on such an error, the tutorials didnt speak of it either. what now? i know i cant continue learning c++ if i cant even compile a simple hello world prog.

---

### Post by skymt on 2006-09-18
You must be using an old book. It's "std::cout" now. You'll understand once you get to namespaces.

---

### Post by mike3k on 2006-09-18
alternately, you could just add
```
using std;
```
after the #include.

---

### Post by po0f on 2006-09-19
```
#include <iostream>
using namespace std;

int main() {
  cout << "Hello world!" << endl;
}
```

Or, alternatively:
```
#include <iostream>
using std::cout;
using std::endl;

int main() {
  cout << "Hello world!" << endl;
}
```

If you're just starting out with C++, I recommend Bruce Eckel's _Thinking in C++_ series of books.  He has generously made them available for free download [here](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html).

---

### Post by vinay_lakhanpal on 2006-10-28
did you use gcc to compile the program. Use g++ to compile and it will work

---

### Post by Dual Cortex on 2006-10-31
> **vinay_lakhanpal said:**
> did you use gcc to compile the program. Use g++ to compile and it will work

Nah, he just forgot to 'add' the std libary

---

### Post by mstation on 2006-11-07
i'll start asking sorry for this but i still don't understand my problem.. im running under ubuntu dapper 6.06.1 and when i try to compile a simple c++ program i get this errors:

> gcc: prova: Nessun file o directory
prova.c: In function ‘main’:
prova.c:8: error: stray ‘\226’ in program
prova.c:8: error: stray ‘\128’ in program
prova.c:8: error: stray ‘\156’ in program
prova.c:8: error: ‘Un’ undeclared (first use in this function)
prova.c:8: error: (Each undeclared identifier is reported only once
prova.c:8: error: for each function it appears in.)
prova.c:8: error: syntax error before ‘solo’
prova.c:8: error: stray ‘\’ in program
prova.c:8: error: stray ‘\226’ in program
prova.c:8: error: stray ‘\128’ in program
prova.c:8: error: stray ‘\157’ in program
prova.c:11: error: stray ‘\226’ in program
prova.c:11: error: stray ‘\128’ in program
prova.c:11: error: stray ‘\156’ in program
prova.c:11: error: ‘Sono’ undeclared (first use in this function)
prova.c:11: error: syntax error before ‘il’
prova.c:11: error: stray ‘\’ in program
prova.c:11: error: stray ‘\226’ in program
prova.c:11: error: stray ‘\128’ in program
prova.c:11: error: stray ‘\157’ in program
prova.c:13: error: stray ‘\226’ in program
prova.c:13: error: stray ‘\128’ in program
prova.c:13: error: stray ‘\156’ in program
prova.c:13: error: stray ‘\226’ in program
prova.c:13: error: stray ‘\128’ in program
prova.c:13: error: stray ‘\157’ in program
prova.c:15: error: stray ‘\226’ in program
prova.c:15: error: stray ‘\128’ in program
prova.c:15: error: stray ‘\156’ in program
prova.c:15: error: stray ‘\’ in program
prova.c:15: error: stray ‘\226’ in program
prova.c:15: error: stray ‘\128’ in program
prova.c:15: error: stray ‘\157’ in program


yes unfortunately its italian but u should still understand well the problem.. the code in prova.c is:

> #include <stdio.h>
#include <stdlib.h>


 main()
{
  int pid;
  printf(“Un solo processo finora\n”);
  pid = fork();
  if (pid==0)
      printf(“Sono il figlio\n”);
  else if (pid > 0)
      printf(“Sono il padre, pid figlio=%d”,pid);
  else
      printf(“Situazione di errore \n”);
}

and yes.. i have installed gcc and the build-essential package..

please help!!

thanks a lot

---

### Post by iovar on 2006-11-08
What are you using to write the file?
You should be using a text-editor like kate,vi,gedit etc. not a 
program like OpenOffice.

---

### Post by mstation on 2006-11-08
i use vi for writing the program.. sometimes i also edit it with gedit..

never used openoffice.. u suggest to rewrite it again with gedit?

any help about how to fix this.. i really need to get it to work for the school exams :(

---

### Post by po0f on 2006-11-08
mstation,

It looks like whatever program you are using to write the program is adding weird characters, “ should be ".  It might have something to do with your locale or input method.

---

### Post by mstation on 2006-11-09
You are right.. im sorry for the disturb.. i just rewrote from zero the code and it compiles perfectly.. thanks again!!

---

