---
title: "Add lpthread in makefile"
date: 2012-11-04
forum: Packaging and Compiling Programs
---

### Post by huangyingw on 2012-11-04
Hi, 
  How to add lpthread option to my makefile? 
  My make command output is as bellow:
```
huangyingw@laptop:/media/volgrp/myproject/git/cplusplus/linux/fundamental/semaphore$ make
g++ -ansi -W -Wall -lstdc++ -I../test -lpthread test.o -o test.exe
test.o: In function `main':
test.cc:(.text+0xbc): undefined reference to `pthread_create'
test.cc:(.text+0xd7): undefined reference to `pthread_create'
test.cc:(.text+0xe8): undefined reference to `pthread_join'
test.cc:(.text+0xf9): undefined reference to `pthread_join'
collect2: error: ld returned 1 exit status
make: *** [test.exe] Error 1
```
the content of my makefile:```
huangyingw@laptop:/media/volgrp/myproject/git/cplusplus/linux/fundamental/semaphore$ cat makefile 
OBJECTS = test.exe
include /home/huangyingw/myproject/git/makefile/GNU_makefile_template
LOCFLAGS = -I../test
LOCFLAGS += -lpthread

```
the content of /home/huangyingw/myproject/git/makefile/GNU_makefile_template:```
huangyingw@laptop:/media/volgrp/myproject/git/cplusplus/linux/fundamental/semaphore$ cat /home/huangyingw/myproject/git/makefile/GNU_makefile_template
CC = g++
CCFLAGS = -ansi -W -Wall -lstdc++
LOCFLAGS =
all: $(OBJECTS)
%.o: %.cc %.cpp
	$(CC) $(CCFLAGS) $(LOCFLAGS) -c $< -o $@
%.exe: %.o
	$(CC) $(CCFLAGS) $(LOCFLAGS) $< -o $@
clean:
	rm -rf *.o core *.stackdump
clobber: clean
	rm -rf *.exe

```

---

### Post by MadCow108 on 2012-11-05
its best to add -pthread to CCFLAGS that handles required compile and link time changes

to only use -lpthread (which you should not) do something like this:
```
LIBS ?= -lpthread

%.exe: %.o
	$(CC) $(CCFLAGS) $(LOCFLAGS) $< $(LIBS) -o $@
```

libraries after objects

---

### Post by huangyingw on 2012-11-05
> **MadCow108 said:**
> its best to add -pthread to CCFLAGS that handles required compile and link time changes

to only use -lpthread (which you should not) do something like this:
```
LIBS ?= -lpthread

%.exe: %.o
	$(CC) $(CCFLAGS) $(LOCFLAGS) $< $(LIBS) -o $@
```

libraries after objects
Great thanks.

---

