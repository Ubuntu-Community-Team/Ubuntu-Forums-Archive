---
title: "makefile with header file issue"
date: 2012-11-04
forum: Packaging and Compiling Programs
---

### Post by huangyingw on 2012-11-04
hi,
  Seems that my makefile did not found my .h file, as make command output shows:```
huangyingw@laptop:~/myproject/git/makefile$ make
g++    -c -o singleton.o singleton.cc
g++ -ansi -W -Wall -lstdc++ -I. singleton.o -o singleton.exe
singleton.o: In function `Singleton::Instance()':
singleton.cc:(.text._ZN9Singleton8InstanceEv[_ZN9Singleton8InstanceEv]+0x8): undefined reference to `Singleton::_instance'
singleton.cc:(.text._ZN9Singleton8InstanceEv[_ZN9Singleton8InstanceEv]+0x34): undefined reference to `Singleton::_instance'
singleton.cc:(.text._ZN9Singleton8InstanceEv[_ZN9Singleton8InstanceEv]+0x3e): undefined reference to `Singleton::_instance'
collect2: error: ld returned 1 exit status
make: *** [singleton.exe] Error 1
rm singleton.o

```
  Following is my makefile ```
huangyingw@laptop:~/myproject/git/makefile$ cat makefile 
CC = g++
CCFLAGS = -ansi -W -Wall -lstdc++
HEADERS = $(wildcard *.h)
OBJECTS = singleton.exe
LOCFLAGS =-I.
all: $(OBJECTS)
%.o: %.cc %.cpp $(HEADERS)
	$(CC) $(CCFLAGS) $(LOCFLAGS) -c $< -o $@
%.exe: %.o
	$(CC) $(CCFLAGS) $(LOCFLAGS) $< -o $@
clean:
	rm -rf *.o core *.stackdump
clobber: clean
	rm -rf *.exe

```
The content of my cc file: ```
huangyingw@laptop:~/myproject/git/makefile$ cat singleton.cc 
#include "stdio.h"
#include "singleton.h"
#include <memory>
int main() {
  printf("hello\n");
  Singleton* singleton= Singleton::Instance();
  return 0;
}

```
The content of my .h file
```
huangyingw@laptop:~/myproject/git/makefile$ cat singleton.h 
#include <memory>
#include <iostream>
using namespace std;

class Singleton {
  public:
    static Singleton * Instance() {
      if( 0== _instance.get())
        _instance.reset( new Singleton);

      return _instance.get();
    }

  protected:
    Singleton(void) {
      cout <<"Create Singleton"<<endl;
    }

    virtual ~Singleton(void) {
      cout << "Destroy Singleton"<<endl;
    }
    friend class auto_ptr<Singleton>;
    static auto_ptr<Singleton> _instance;
};

```

---

### Post by spjackson on 2012-11-04
It is finding your .h file, or you would get different errors.

singleton.h declares the static Singleton::_instance but it is not defined anywhere. You need a line outside the class definition that looks like this.
```

auto_ptr<Singleton> Singleton::_instance;

```
The normal place to put this would be in the .cc file for the class (i.e. the class implementation file). If you put it in the header file, then you need to worry about multiple defines when the header gets included in multiple sources.

---

### Post by huangyingw on 2012-11-04
> **spjackson said:**
> It is finding your .h file, or you would get different errors.

singleton.h declares the static Singleton::_instance but it is not defined anywhere. You need a line outside the class definition that looks like this.
```

auto_ptr<Singleton> Singleton::_instance;

```
The normal place to put this would be in the .cc file for the class (i.e. the class implementation file). If you put it in the header file, then you need to worry about multiple defines when the header gets included in multiple sources.
Hi, great thanks.

---

