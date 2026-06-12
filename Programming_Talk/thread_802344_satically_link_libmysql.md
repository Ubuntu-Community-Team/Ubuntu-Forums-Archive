---
title: "satically link libmysql"
date: 2008-05-21
forum: Programming Talk
---

### Post by kirys on 2008-05-21
hi all 
I'm trying to compile a small program of my, but i have to link it statically cause it must be used on a server I cannot "control".
But when i try to compile the code i get:

```
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c main.cpp -o main.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c kshmutils.c -o kshmutils.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c cfgloader.cpp -o cfgloader.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c statusanalyzer.cpp -o statusanalyzer.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c mysqlwrapper.cpp -o mysqlwrapper.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c kutils.cpp -o kutils.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql -c enginecore.cpp -o enginecore.o
g++ -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static -I/usr/include/mysql ./main.o -L/usr/lib/mysql -lmysqlclient -L/tmp/mysql -lmysqlclient ./kshmutils.o ./cfgloader.o ./statusanalyzer.o ./mysqlwrapper.o ./enginecore.o ./kutils.o -o ./uosengine
./statusanalyzer.o: In function `StatusAnalyzer::ckUOActive()':
statusanalyzer.cpp:(.text+0x208): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
./mysqlwrapper.o: In function `mysqlINIT()':
mysqlwrapper.cpp:(.text+0xba): undefined reference to `mysql_server_init'
./mysqlwrapper.o: In function `MysqlWrapper::doUpdateQuery(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
mysqlwrapper.cpp:(.text+0xde): undefined reference to `mysql_query'
mysqlwrapper.cpp:(.text+0xf3): undefined reference to `mysql_error'
./mysqlwrapper.o: In function `MysqlWrapper::selectDB(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
mysqlwrapper.cpp:(.text+0x138): undefined reference to `mysql_select_db'
./mysqlwrapper.o: In function `MysqlWrapper::fetchFields()':
mysqlwrapper.cpp:(.text+0x1a1): undefined reference to `mysql_num_fields'
mysqlwrapper.cpp:(.text+0x1ba): undefined reference to `mysql_fetch_fields'
./mysqlwrapper.o: In function `MysqlWrapper::freeResults()':
mysqlwrapper.cpp:(.text+0x667): undefined reference to `mysql_free_result'
./mysqlwrapper.o: In function `MysqlWrapper::doQuery(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
mysqlwrapper.cpp:(.text+0x742): undefined reference to `mysql_query'
mysqlwrapper.cpp:(.text+0x752): undefined reference to `mysql_error'
mysqlwrapper.cpp:(.text+0x779): undefined reference to `mysql_store_result'
./mysqlwrapper.o: In function `MysqlWrapper::Close()':
mysqlwrapper.cpp:(.text+0x7c4): undefined reference to `mysql_close'
./mysqlwrapper.o: In function `MysqlWrapper::Connect()':
mysqlwrapper.cpp:(.text+0x820): undefined reference to `mysql_init'
mysqlwrapper.cpp:(.text+0x856): undefined reference to `mysql_real_connect'
mysqlwrapper.cpp:(.text+0x86b): undefined reference to `mysql_error'
./mysqlwrapper.o: In function `MysqlWrapper::doFetch()':
mysqlwrapper.cpp:(.text+0x8ab): undefined reference to `mysql_num_fields'
mysqlwrapper.cpp:(.text+0x8f3): undefined reference to `mysql_fetch_row'
mysqlwrapper.cpp:(.text+0x90b): undefined reference to `mysql_fetch_lengths'
./mysqlwrapper.o: In function `mysqlEND()':
mysqlwrapper.cpp:(.text+0x95): undefined reference to `mysql_server_end'
collect2: ld returned 1 exit status
make: *** [executable] Error 1

```

I think I'm missing something but i don't know what
I'm compiling under kubuntu 7.10 with gcc 4.1.3
Thank you
Kirys

---

### Post by dwhitney67 on 2008-05-21
Have you tried placing a -static before each of the libraries that you use.  Something like:
```
... -static libA -static libB ...
```

If you don't already have a Makefile, I would suggest creating one.

It also appears that you are specifying -static when compiling the object files.  This is not necessary.  You should only specify -static at the link stage.

And personally, I always like to collect my object files first, then specify the external libraries that I will link in to form the executable.  Something like:

```
SRCS     := source1.cpp source2.cpp etc.cpp
OBJS     := $(SRCS:.cpp=.o)
CXXFLAGS := -Wall -pedantic
INCPATHS := -I/usr/include/mysql
LIBPATHS := -L/usr/lib/mysql -LotherPath
LIBS     := -static -lmysqlclient -lotherLib
EXE      := MyExecutable

...

$(EXE): $(OBJS)
        $(CXX) $(OBJS) $(LIBPATHS) $(LIBS) -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) $(INCPATHS) -c $< -o $@

...
```

---

### Post by kirys on 2008-05-21
I already use a make file and i'm using mysql_config --libs and --include storing the result into variables and so on.
The -static  parameter is that way just because i put that into the cflags var i'll make a linkflags var so it is cleaner

your makefile is much more cleaner that mine
anyway here is it mine ^_^
```

CC=g++
LINKER=${CC}
EXECUTABLE=uosengine
MYSQL_INC=${shell mysql_config --include}
MYSQL_LNK=${shell mysql_config --libs}
DEBUG=-D _DEBUGMODE_
FLAGS=-Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing -static-libgcc -static ${MYSQL_INC}
#FLAGS=-Wall ${MYSQL_INC} -g ${DEBUG} 
TOLINK=${MYSQL_LNK} -L/tmp/mysql -lmysqlclient ./kshmutils.o ./cfgloader.o ./statusanalyzer.o ./mysqlwrapper.o ./enginecore.o ./kutils.o
default : all

clean :
	-rm ./*.o
	-rm ./$(EXECUTABLE)
	-rm ./*~


main.o: main.cpp
	${CC} ${FLAGS} -c main.cpp -o main.o

cfgloader.o: cfgloader.cpp
	${CC} ${FLAGS} -c cfgloader.cpp -o cfgloader.o

statusanalyzer.o: statusanalyzer.cpp
	${CC} ${FLAGS} -c statusanalyzer.cpp -o statusanalyzer.o

mysqlwrapper.o: mysqlwrapper.cpp
	${CC} ${FLAGS} -c mysqlwrapper.cpp -o mysqlwrapper.o

kshmutils.o: kshmutils.c
	${CC} ${FLAGS} -c kshmutils.c -o kshmutils.o

kutils.o: kutils.cpp
	${CC} ${FLAGS} -c kutils.cpp -o kutils.o

enginecore.o: enginecore.cpp
	${CC} ${FLAGS} -c enginecore.cpp -o enginecore.o

tester.o: tester.cpp
	${CC} ${FLAGS} -c tester.cpp -o tester.o

executable: main.o kshmutils.o cfgloader.o statusanalyzer.o mysqlwrapper.o kutils.o enginecore.o
	${LINKER} ${FLAGS} ./main.o ${TOLINK} -o ./${EXECUTABLE}

all : executable


```

---

### Post by dwhitney67 on 2008-05-21
Please see if the Makefile below works for you.

Besides cleaning up your original Makefile to make it simpler and easier to read, I also modified the value derived for MYSQL_LNK.  If you were to run your original command on the command-line, you would notice that it also returns the '-lmysqlclient' library name.  However since you wanted to statically link this in, I believe what I provided below should work (and perhaps it is not necessary).

```
SRCS       = $(wildcard *.cpp)
OBJS       = $(SRCS:.cpp=.o)

DEBUG      = -D_DEBUGMODE_

MYSQL_INC := ${shell mysql_config --include}
MYSQL_LNK := ${shell mysql_config --libs | cut -d ' ' -f1}

CXXFLAGS   = -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing $(MYSQL_INC)
#CXXFLAGS   = -Wall $(MYSQL_INC) -g $(DEBUG)

DEP_FILE   = .depend

TOLINK     = $(MYSQL_LNK) -static -lmysqlclient
EXE        = uosengine

.PHONY: clean


$(EXE): $(OBJS)
	@echo linking $@
	@$(CXX) $^ $(TOLINK) -o $@

.cpp.o:
	@echo compiling $<
	@$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	$(RM) $(OBJS)
	$(RM) $(EXE)
	$(RM) ./*~

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
```

---

### Post by kirys on 2008-05-21
First I want to thank you for your help

I've tried the Makefile you suggested but doesn't seem to work
```
Makefile - building dependencies in: .depend
compiling cfgloader.cpp
compiling enginecore.cpp
compiling kutils.cpp
compiling main.cpp
compiling mysqlwrapper.cpp
compiling statusanalyzer.cpp
compiling tester.cpp
linking uosengine
tester.o: In function `main':
tester.cpp:(.text+0xd0): multiple definition of `main'
main.o:main.cpp:(.text+0xc0): first defined here
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(mf_pack.o): In function `unpack_dirname':
(.text+0x5b6): warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(libmysql.o): In function `read_user_name':
(.text+0x57ef): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(mf_pack.o): In function `unpack_dirname':
(.text+0x5c5): warning: Using 'endpwent' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
statusanalyzer.o: In function `StatusAnalyzer::ckUOActive()':
statusanalyzer.cpp:(.text+0x208): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(my_gethostbyname.o): In function `my_gethostbyname_r':
(.text+0x30): warning: Using 'gethostbyname_r' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(libmysql.o): In function `mysql_server_init':
(.text+0x6136): warning: Using 'getservbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
enginecore.o: In function `ChildClass::checkDone()':
enginecore.cpp:(.text+0xd1): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0xef): undefined reference to `mutexSignal(int)'
enginecore.o: In function `ChildClass::getItem()':
enginecore.cpp:(.text+0x12b): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0x16c): undefined reference to `mutexSignal(int)'
enginecore.o: In function `ChildClass::saveItem()':
enginecore.cpp:(.text+0x1c3): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0x20f): undefined reference to `mutexSignal(int)'
enginecore.cpp:(.text+0x251): undefined reference to `mutexSignal(int)'
enginecore.o: In function `EngineCore::toDo()':
enginecore.cpp:(.text+0x283): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0x290): undefined reference to `mapShm(int)'
enginecore.cpp:(.text+0x2c9): undefined reference to `unmapShm(void*)'
enginecore.cpp:(.text+0x2d6): undefined reference to `mutexSignal(int)'
enginecore.o: In function `EngineCore::checkDone()':
enginecore.cpp:(.text+0x300): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0x30d): undefined reference to `mapShm(int)'
enginecore.cpp:(.text+0x322): undefined reference to `unmapShm(void*)'
enginecore.cpp:(.text+0x32f): undefined reference to `mutexSignal(int)'
enginecore.o: In function `EngineCore::allocate(std::vector<ServerInfo, std::allocator<ServerInfo> >&)':
enginecore.cpp:(.text+0x403): undefined reference to `genenerateKey(char const*, char)'
enginecore.cpp:(.text+0x410): undefined reference to `getMutex(int)'
enginecore.cpp:(.text+0x41c): undefined reference to `destroyMutex(int)'
enginecore.cpp:(.text+0x429): undefined reference to `createMutex(int)'
enginecore.cpp:(.text+0x447): undefined reference to `genenerateKey(char const*, char)'
enginecore.cpp:(.text+0x454): undefined reference to `getShm(int)'
enginecore.cpp:(.text+0x460): undefined reference to `deallocateShm(int)'
enginecore.cpp:(.text+0x47f): undefined reference to `allocateShm(int, int)'
enginecore.cpp:(.text+0x494): undefined reference to `mapShm(int)'
enginecore.cpp:(.text+0x513): undefined reference to `unmapShm(void*)'
enginecore.o: In function `EndCore(int)':
enginecore.cpp:(.text+0x5a0): undefined reference to `deallocateShm(int)'
enginecore.cpp:(.text+0x5b1): undefined reference to `destroyMutex(int)'
enginecore.o: In function `EngineCore::removeChild(int)':
enginecore.cpp:(.text+0x80d): undefined reference to `mutexWait(int)'
enginecore.cpp:(.text+0x81a): undefined reference to `mapShm(int)'
enginecore.cpp:(.text+0x897): undefined reference to `unmapShm(void*)'
enginecore.cpp:(.text+0x8a4): undefined reference to `mutexSignal(int)'
enginecore.o: In function `ChildClass::ChildClass(int, int, int, unsigned int)':
enginecore.cpp:(.text+0x165e): undefined reference to `mapShm(int)'
enginecore.o: In function `EngineCore::saveResults()':
enginecore.cpp:(.text+0x2eb5): undefined reference to `mapShm(int)'
enginecore.cpp:(.text+0x2f93): undefined reference to `unmapShm(void*)'
enginecore.o: In function `ChildClass::~ChildClass()':
enginecore.cpp:(.text+0x4079): undefined reference to `unmapShm(void*)'
enginecore.o: In function `ChildClass::ChildClass(int, int, int, unsigned int)':
enginecore.cpp:(.text+0x4d5e): undefined reference to `mapShm(int)'
enginecore.o: In function `ChildClass::~ChildClass()':
enginecore.cpp:(.text+0x4ec9): undefined reference to `unmapShm(void*)'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(yassl_int.o): In function `yaSSL::yassl_int_cpp_local2::GetSelf()':
(.text+0x1cc3): undefined reference to `pthread_self'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(my_compress.o): In function `my_uncompress':
(.text+0x60): undefined reference to `uncompress'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libmysqlclient.a(my_compress.o): In function `my_compress_alloc':
(.text+0x102): undefined reference to `compress'
collect2: ld returned 1 exit status
make: *** [uosengine] Error 1

```
The multiple main() problem is caused by the tester.cpp source that contains the blackbox tests, so I've removed it but the other problems remain.

I've spent all day trying to compile this program and another unsuccessfully (they do both link dynamically without a problem).
I've also noticed that some .a files (the static libs) are missing even though the corresponding -dev package is installed, I've started to think that this may be related to that.

I didn't thought that make a static binary would have been so difficult ^_^, Java made me dumb :P

Maybe I could upload the linked libraries in the same directory of the executable,could it work?
How can I get all dependencies of my prog when it is dinamically linked, and there is a way to say the program where to search the libs at run time?


I'll continue investigate tomorrow
Thank you again for your help
Bye
Kirys

---

### Post by dwhitney67 on 2008-05-21
Many of the errors seem to be the result of a missing library (-ies) or object file(s).  Where are the following methods/functions implemented?
```
mutexWait(int)
mutexSignal(int)
mapShm(int)
unmapShm(void*)
etc
```

For the undefined reference to pthread_self(), this function is included in libpthread.a.  You will need to augment TOLINK to include -lpthread.
```
TOLINK += -lpthread
```

If you wish to retain your test program in the current directory, then you can do so... however, you will need to modify the SRCS in the Makefile to explicitly list your application's source files.  For instance:
```
SRCS = file1.cpp \
       file2.cpp \
       ...       \
       fileN.cpp

```

P.S.  Also re-add the -lstatic-libgcc to TOLINK as you originally had it in your Makefile.

---

### Post by kirys on 2008-05-21
kshmutils.c|h 

I'l convert the SRCS as explicit.

I have to study the Makefile format much more :)

---

### Post by dwhitney67 on 2008-05-21
Ah... that explains the linker problems.  The Makefile you tested earlier did not pick up the C file kshmutils.c.

Create a new variable called CSRCS and set that equal to kshmutils.c, along with other supporting stuff within the Makefile.
```

CSRCS = kshmutils.c
COBJS = $(CSRCS:.c=.o)

...

$(EXE): $(OBJS) $(COBJS)
	@echo linking $@
	@$(CXX) $^ $(TOLINK) -o $@

...

.c.o:
	@echo compiling $<
	@$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	$(RM) $(OBJS) $(COBJS)
	$(RM) $(EXE)
	$(RM) ./*~

...

$(DEP_FILE):
	@echo Building dependencies in: $@
	@$(CXX) -E -MM $(SRCS) $(CSRCS) >> $(DEP_FILE)

```

---

### Post by kirys on 2008-05-21
This modified version of the makefile seems to work, it seems that adding this "-lz -lpthread -lcrypt -lm -lssl" (plus the .c related lines) actually suffice for the static link of this program.

```
LM=static
MODE=main

ifeq ($(MODE),main)
CSRCS=kshmutils.c
SRCS	= \
	cfgloader.cpp\
	enginecore.cpp\
	kutils.cpp\
	main.cpp\
	mysqlwrapper.cpp\
	statusanalyzer.cpp
else
CSRCS=kshmutils.c
SRCS	= \
	cfgloader.cpp\
	enginecore.cpp\
	kutils.cpp\
	mysqlwrapper.cpp\
	statusanalyzer.cpp\
	tester.cpp
endif

OBJS       = $(SRCS:.cpp=.o) $(CSRCS:.c=.o)

DEBUG      = -D_DEBUGMODE_

MYSQL_INC := ${shell mysql_config --include}
MYSQL_LNK := ${shell mysql_config --libs} -lz -lpthread -lcrypt -lm -lssl 

CXXFLAGS   = -Wall -march=pentium3 -m32 -O2 -fno-strict-aliasing $(MYSQL_INC)
#CXXFLAGS   = -Wall $(MYSQL_INC) -g $(DEBUG)

DEP_FILE   = .depend

ifeq ($(LM),static)
TOLINK     = $(MYSQL_LNK) -static -static-libgcc
else 
TOLINK     = $(MYSQL_LNK)
endif

EXE        = uosengine

.PHONY: clean


$(EXE): $(OBJS)
	@echo linking $@
	@$(CXX) $^ $(TOLINK) -o $@

.cpp.o:
	@echo compiling $<
	@$(CXX) $(CXXFLAGS) -c $< -o $@

.c.o:
	@echo compiling $<
	@$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	$(RM) $(OBJS)
	$(RM) $(EXE)
	$(RM) ./*~
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(SRCS) $(CSRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
```

Thank you I've learned a lot on Makefiles!
Kirys

---

### Post by dwhitney67 on 2008-05-21
I'm glad you got it working!

Here's one more thing to consider (and that's the += operator)...
```

...

CSRCS = kshmutils.c

SRCS  = cfgloader.cpp \
        enginecore.cpp \
        kutils.cpp \
        mysqlwrapper.cpp \
        statusanalyzer.cpp

ifeq ($(MODE),main)
SRCS += main.cpp
else
SRCS += tester.cpp
endif

...
```

---

### Post by kirys on 2008-05-22
Thank you again :)

---

