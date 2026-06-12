---
title: "make issue"
date: 2011-10-13
forum: Packaging and Compiling Programs
---

### Post by huangyingw on 2011-10-13
Hello
    I use the following makefile ```
huangyingw@work:~/data_structure/cirQueue$ cat makefile 
main:
	g++ -shared CirQueue.cc -o CirQueue.so
	gcc -L. test.cc -o test -lCirQueue
	export LD_LIBRARY_PATH=.

```to compile, and encounter this issue:
```
huangyingw@work:~/data_structure/cirQueue$ make
g++ -shared CirQueue.cc -o CirQueue.so
/usr/bin/ld: /tmp/ccjAGDgo.o: relocation R_X86_64_32 against `.bss' can not be used when making a shared object; recompile with -fPIC
/tmp/ccjAGDgo.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [main] Error 1

```
    Could some one do me a favor on this issue?

---

### Post by SevenMachines on 2011-10-13
Did you do as it says and recompile with -fPIC? Gentoo has a better explanation why than I could knock together
[http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3](http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3)

---

### Post by SevenMachines on 2011-10-13
Oh, and g++ for c++ files, gcc for c. Generally I'd say its standard practice to call a library libcirqueue.so rather than without the prefix, or in upper case. You'd probably want to version the filename to but I'm rambling :)

---

### Post by huangyingw on 2011-10-13
yes, I have updated my makefile as following:
```
main:
	g++ -fPIC -shared CirQueue.cc -o libCirQueue.so
	g++ -fPIC -L. test.cc -o test -lCirQueue
	export LD_LIBRARY_PATH=.

```
While it give me this error:
```
huangyingw@work:~/data_structure/cirQueue$ make
g++ -fPIC -shared CirQueue.cc -o libCirQueue.so
g++ -fPIC -L. test.cc -o test -lCirQueue
/tmp/ccuKig1B.o: In function `main':
test.cc:(.text+0x83): undefined reference to `CirQueue<int>::InitQueue()'
test.cc:(.text+0x9d): undefined reference to `CirQueue<int>::EnQueue(int)'
collect2: ld returned 1 exit status
make: *** [main] Error 1

```
Bellowing is the output of nm command:
```
huangyingw@work:~/data_structure/cirQueue$ nm libCirQueue.so |grep InitQueue
huangyingw@work:~/data_structure/cirQueue$ 

```
The content of my CirQueue.h file as bellow:
```
huangyingw@work:~/data_structure/cirQueue$ cat CirQueue.h
#include <iostream>
using namespace std;
#define QueueSize 10

template <class Type> class CirQueue
{               
  public:
    int front;
    int rear;
    int count;
    Type data[QueueSize];
    int QueueEmpty();
    Type DeQueue();
    int QueueFront();
    void InitQueue();
    void Error(char* message);
    int QueueFull();
    void EnQueue(Type x);
};

```

---

### Post by SevenMachines on 2011-10-14
No idea whats in you CirQueue.cc file but since you're using templates, you need declaration and definition in the same file, ie, declare and implement your functions in CirQueue.h

---

### Post by SevenMachines on 2011-10-14
cplusplus is always a classic source of good explanations :)
[http://www.cplusplus.com/doc/tutorial/templates/](http://www.cplusplus.com/doc/tutorial/templates/)

---

### Post by huangyingw on 2011-10-14
> **SevenMachines said:**
> No idea whats in you CirQueue.cc 
I have cut them to be as small as possible, while keeping the same error recurring.
test.cc:
```
huangyingw@work:~/data_structure/cirQueue$ cat test.cc 
#include "CirQueue.h"
int main()
{
  CirQueue<int>* Q=new CirQueue<int>();
  Q->InitQueue();
  return 0;
}

```
CirQueue.cc
```
huangyingw@work:~/data_structure/cirQueue$ cat CirQueue.cc 
#include "CirQueue.h"

template<class Type> void CirQueue<Type>::InitQueue()
{
}

```
CirQueue.h
```
huangyingw@work:~/data_structure/cirQueue$ cat CirQueue.h
#include <iostream>
using namespace std;

template <class Type> class CirQueue
{               
  public:
    void InitQueue();
};

```
Help me with a glance?

---

### Post by SevenMachines on 2011-10-14
Using the essential sections of the previous link 
[http://www.cplusplus.com/doc/tutorial/templates/](http://www.cplusplus.com/doc/tutorial/templates/)

(1) > When projects grow it is usual to split the code of a  program in  different source code files. In these cases, the interface  and  implementation are generally separated. Taking a library of  functions as  example, the interface generally consists of declarations  of the  prototypes of all the functions that can be called. These are  generally  declared in a "header file" with a .h extension, and the  implementation  (the definition of these functions) is in an independent  file with c++  code.

Because templates are compiled when required, this forces a restriction   for multi-file projects: the implementation (definition) of a template   class or function must be in the same file as its declaration. That   means that we cannot separate the interface in a separate header file,   and that we must include both interface and implementation in any file   that uses the templates.You can't have CirQueue.h declare a class template and have CirQueue.cc implement its functions, generally you'd have no CirQueue.cc and just put the implementation in CirQueue.h, for example.

CirQueue.h:
```
#include <iostream>
using namespace std;

template <class Type> class CirQueue
{
  public:
    void InitQueue(){
    std::cout<<"InitQueue()"<<std::endl;
  }
};

```(2) > From the point of view of the compiler, templates are not normal  functions or classes. They are compiled on demand, meaning that the code  of a template function is not compiled until an instantiation with  specific template arguments is required. So whats there to make a library out of? Nothing, so skip the library creation step, include the CirQueue.h header in test.cc as you have done and compile...
```
$ g++ -o test test.cc
$ $ ./test 
InitQueue()
```I'd suggest you read the cplusplus link above, templates are very useful, but different, and you need to learn how to use them properly.

---

### Post by SevenMachines on 2011-10-14
Just to add, you might want to get a moderator to move this to the programming forum, its more active and there'll be more c++ programmers, this isnt really a compiling issue anymore

---

### Post by huangyingw on 2011-10-15
> **SevenMachines said:**
> Using the essential sections of the previous link 
[http://www.cplusplus.com/doc/tutorial/templates/](http://www.cplusplus.com/doc/tutorial/templates/)

Yes, thank you for your detail explanation, I will read the URL you suggest carefully.

---

