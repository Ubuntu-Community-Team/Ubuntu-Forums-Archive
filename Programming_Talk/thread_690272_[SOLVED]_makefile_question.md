---
title: "[SOLVED] makefile question"
date: 2008-02-07
forum: Programming Talk
---

### Post by Houman on 2008-02-07
hi folks, 
I have this big makefile that I have been using for a while and I think i copied it from somewhere on the internet a while back; all i do is just change the source file names  and it does the work for me using implicit rules;

however recently I have noticed that my compilation times are getting very long, and in fact i noticed when i change one of the files in th project and  recompile it seems to be recompiling everything (I think, because if i edit file x.cpp i still see warnings related to file y.cpp), 

I was wondering if someone could please take a look at this makefile and tell me if there is anything i can do to make the compile time faster? 

thank you so much, and here is the makefile:

```

PROG = myexec

# The name of the dependency file
DEPENDF = .depend

SRC=main.c x.cpp y.cpp q.cpp 

INC = -I../inc -Ilibs/SVL/include/
CFLAGS   = -g -Wall $(INC)
CXXFLAGS = $(INC) -Wall  -g  
-march=pentium4  # for speed
# Linker directories
LDLIBS = -Llibs/SVL/lib/ -lsvl.dbg


LDFLAGS  = $(LDLIBS)  
CXX = g++
CC = g++
CCOBJS = $(SRC:.cc=.o)
OBJS = $(CCOBJS:.c=.o)

all:	do-it-all

# create the dependency file and redo the make if required
ifeq ($(DEPENDF),$(wildcard $(DEPENDF)))
include $(DEPENDF)
do-it-all: $(PROG)
else
do-it-all: lib depend
	@echo "Re-doing make"
	$(MAKE)
endif

$(PROG): $(OBJS)
	$(CXX) $(CXXFLAGS) -o $@ $(OBJS) $(LDFLAGS)
lib:
	 $(MAKE) -C libs/SVL/
clean:
	rm -f core* *.o *% *~ $(DEPENDF) $(PROG)

depend:
	@echo "Doing a \"make depend\""
	$(CXX) -MM $(INC) $(SRC) > $(DEPENDF)

```


thanks again;

Houman

---

### Post by lnostdal on 2008-02-07
may i suggest trying cmake (or scons) instead .. it will save you much trouble -- and it already figures out dependencies and thus only compile files that need to be compiled etc.

---

### Post by Houman on 2008-02-07
hi there;

thanks for the reply, i am checking out cmake right now, 

but I will probably not be able to use cmake for this project since im in the project with several other people;

if i could only find out why this makefile recompiles everythign every time it would be great, but i cant seem to be finding the reason :confused:


thanks for your reply;

Houman

---

### Post by stroyan on 2008-02-07
The dependencies between the source files is being created automatically by using 'g+ -MM'.
What rules are are written in the .depend file?
Perhaps there really has been a change in the source that makes more files depend on each other.

Another possible cause of excessive rebuilding is having files shared between systems that don't keep their clocks well synchronized.
An edit by a system with a fast clock could leave make operations on other systems rebuilding many files many times as the newly rebuilt files would not look newer than the files they depend on.

---

### Post by Houman on 2008-02-12
hi there, 

sorry for the late reply;

I am looking through my generated .depend file and there is  nothing that would indicate the compiler should recompile y.cpp wen i change x.cpp, i mean there is something like this: 

```

x.o: x.cpp   x.h  globals.h  a.h b.h c.h
y.cpp: y.cpp y.h globals.h  a.h b.h c.h

```
The bottom line is that the y.cpp list of dependencies doesnt include x.cpp , so im very puzzled why is y.cpp is compiled when i edit x.cpp (not its header file, just the cpp file);

thanks for your help

Houman

---

### Post by stroyan on 2008-02-12
It seems like some file time is not as it should be.
You can run 'make -db' to get a detailed report of what make is thinking.
It may show a newer prerequisite file that you thought was older.

---

### Post by Houman on 2008-02-12
nice, that was a handy little command, thanks;

it showed that nothing is happening out of the ordinary, it seems y.cpp is not being recompiled after all , i think the reason I thought y.cpp is being recompiled is because i kept seeing warnings from y.cpp file even though i had changed x.cpp and y.cpp had no business being recompiled, 
however i did a little experiment, i compiled everything, then i deleted the executable (leaving all object files) then I only ran the command necessary to link the objects and create the executable (and this shouldn't recompile anything obviously, just links the .o files) and guess what, it gave me all those warnings from y.cpp again, so i guess i was lead into thinking y.cpp is being compiled just because the linker gives out warnings too (I guess).

I'm still confused a bit, especially since my compile time is pretty high, but i think there is nothing i can do about that ( i guess i could look into using precompiled headers);


thanks for your help stroyan;

Houman

---

### Post by Houman on 2008-02-21
hi there;

I solved my own problem and decided to post the solution, the problem is that i had a mixture of cpp and c files and the objects variable in the makefile wasnt containing the right strings, i had to change:

```

CCOBJS = $(SRC:.cc=.o)
OBJS = $(CCOBJS:.c=.o)

```

to
```

CCOBJS = $(SRC:.cpp=.o)
OBJS = $(CCOBJS:.c=.o)

```

because i have c files and cpp files rather than c and cc files, also if you have a mix of cpp files and c files and you have a makefile that has a line like this:
```

     SOURCES = source1.c source2.cpp sourceN.c # List of source code
     OBJECTS = $(SOURCES:.cpp=.o)

```
 then source1.o will never be created and every time you compile the compiler recompiles the source1.c even if it has not been changed; so you got to make sure you change the cpp files AND c files into o files in the makefile;

regards

Houman

---

