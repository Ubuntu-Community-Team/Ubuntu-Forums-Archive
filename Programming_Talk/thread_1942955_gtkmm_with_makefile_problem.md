---
title: "gtkmm with makefile problem"
date: 2012-03-18
forum: Programming Talk
---

### Post by marcux on 2012-03-18
Hello all!
I have exactly the same problem as in stackoverflow:

[http://stackoverflow.com/questions/6...file-and-gtkmm]("http://stackoverflow.com/questions/6442550/problem-with-makefile-and-gtkmm")

There they don't find any solution, so I hope you can help me.
The problem is that when I compile in my terminal with:
g++ main.cpp -o output `pkg-config gtkmm-2.4 --cflags --libs`
The compilation goes fine.
When I write it in my makefile I get the error that it
can not find Gtkmm, and I can see that make writes the same command
in the terminal.
The only thing I have done is to put include <gtkmm.h> into my file.
If I run pkg-config --cflags in terminal /use/include/gtkmm-2.4 exists 
In the answer I get back.
There must be some difference when I compile it and when it goes through make?
What is the problem?
What to do?

Many thanks in advance!
Marcux

---

### Post by SevenMachines on 2012-03-19
You'd need to post at least the makefile to know what the problem is. I'd guess that somewhere you're actually relying on makefiles implicit rules for a compilation step, like making a .o from a .c or something like that. Implicit rules use CXXFLAGS though so you can try something like
```
 CXXFLAGS += $(shell pkg-config --cflags gtkmm-2.4)
```at the top of the makefile. but as i say, difficult to know without any code.

[EDIT]
Looking at the link you posted, thats exactly his problem, creating  main.o from main.cc is left to makefiles implicit rules to do.

---

### Post by marcux on 2012-03-19
Sorry, here is my makefile:
```

OBJS = files.o main.o xmlstr.o date.o staff/staff.o staff/job.o project/project.o project/activity.o
CC = g++
CFLAGS = -Wall -c
LFLAGS = -Wall
GTKFLAGS = `pkg-config gktmm-2.4 --cflags --libs`

handleproject : $(OBJS)
    $(CC) $(LFLAGS) $(OBJS) -o handleproject $(GTKFLAGS)

files.o : project/project.h project/activity.h staff/staff.h saveobj.h files.h files.cpp
    $(CC) $(CFLAGS) files.cpp

main.o : project/project.h staff/job.h staff/staff.h xmlstr.h files.h main.cpp
    $(CC) $(CFLAGS) main.cpp $(GTKFLAGS)

xmlstr.o : xmlstr.h xmlstr.cpp
    $(CC) $(CFLAGS) xmlstr.cpp

date.o : date.h date.cpp
    $(CC) $(CFLAGS) date.cpp

staff/staff.o : xmlstr.h saveobj.h staff/staff.h staff/staff.cpp
    $(CC) $(CFLAGS) staff/staff.cpp -o staff/staff.o

staff/job.o : xmlstr.h saveobj.h staff/job.h staff/job.cpp
    $(CC) $(CFLAGS) staff/job.cpp -o staff/job.o

project/project.o : xmlstr.h saveobj.h date.h files.h staff/staff.h project/activity.h project/project.h project/project.cpp
    $(CC) $(CFLAGS) project/project.cpp -o project/project.o

project/activity.o : xmlstr.h saveobj.h date.h project/activity.h project/activity.cpp
    $(CC) $(CFLAGS) project/activity.cpp -o project/activity.o

clean :
    \rm *.o *~ handleproject staff/*.o staff/*~ project/*.o project/*~

```

I hope this helps.
I am not so experienced in making makefiles.
Many thanks!

---

### Post by SevenMachines on 2012-03-19
You'd need to check your spelling for one, GTKFLAGS will be empty as you have it now since its not
```
 GTKFLAGS = `pkg-config gktmm-2.4 --cflags --libs`
```you've misspelled gtkmm, so its
```
GTKFLAGS = `pkg-config gtkmm-2.4 --cflags --libs`
```

---

### Post by marcux on 2012-03-19
I am so embarressed, what a misstake!!
Thanks alot SevenMachines!!
I have been stairing at my file over and over again, without seeing that obvious misstake!

Thanks again SevenMachines!

---

### Post by SevenMachines on 2012-03-19
Happens to us all, usually more than we'd like to admit :)

---

### Post by anewguy on 2012-03-19
Years and years ago when I was a systems programmer and systems administrator on what are now great big iron boat anchors, I had a programmer come up to me and ask that I add some form of translator for him if he was using an editor for a COBOL program - seems he always typed  the word "SPACES" as "SAPCES" and was getting tired of all the compilation errors!

Dave ;)

---

