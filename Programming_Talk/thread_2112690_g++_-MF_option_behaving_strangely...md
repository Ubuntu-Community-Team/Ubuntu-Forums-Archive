---
title: "g++ -MF option behaving strangely.."
date: 2013-02-05
forum: Programming Talk
---

### Post by letsplayfootsy on 2013-02-05
Hey everyone,
Not sure if this is a bug or user error (probably the latter, as it would be a pretty big bug).

When I'm trying to compile a dependency list for Make using g++ -MM, the -MF option for specifying a file does not seem to work properly.. anyone have any idea what I'm doing wrong?

The following command WORKS:
g++ -g -O0 -Wall -Wno-unused-variable -Wno-sign-compare -DLINUX -MM BGrid2d.cpp Flux.cpp ImplicitEuler.cpp RK2.cpp Solver2d.cpp Source.cpp VelStore2d.cpp BGrid2d.h Flux.h ImplicitEuler.h RK2.h Solver2d.h Source.h VelStore2d.h > ./.depend

The following command DOES NOT WORK PROPERLY
g++ -g -O0 -Wall -Wno-unused-variable -Wno-sign-compare -DLINUX -MM -MF"./.depend" BGrid2d.cpp Flux.cpp ImplicitEuler.cpp RK2.cpp Solver2d.cpp Source.cpp VelStore2d.cpp BGrid2d.h Flux.h ImplicitEuler.h RK2.h Solver2d.h Source.h VelStore2d.h

The difference in files is that the first command outputs correctly the entire list of objects and dependencies. The second command only writes the final line of the output of the first command. I'm at a loss as to why it would do that....

---

### Post by r-senior on 2013-02-05
I suspect it generates the output for each .cpp file listed in the command and overwrites the output file for each one such that you only end up with the last.

---

### Post by letsplayfootsy on 2013-02-05
Hmm, that's interesting... I guess my next question should be, Is this the expected behaviour? If so, how do I get it to do what I want? i.e. a single file listing all the dependencies, each on different lines?

---

### Post by r-senior on 2013-02-05
The GNU make documentation recommends one dependency file for each source file, which would be consistent with the behaviour.

[http://www.gnu.org/software/make/manual/html_node/Automatic-Prerequisites.html](http://www.gnu.org/software/make/manual/html_node/Automatic-Prerequisites.html)

This approach looks a bit more palatable than the sed construct that GNU suggest:

[http://scottmcpeak.com/autodepend/autodepend.html](http://scottmcpeak.com/autodepend/autodepend.html)

The other possibility is to use GNU autotools rather than rolling your own, where automake will generate the makefiles.

[http://www.gnu.org/software/automake/manual/html_node/Dependency-Tracking.html#Dependency-Tracking](http://www.gnu.org/software/automake/manual/html_node/Dependency-Tracking.html#Dependency-Tracking)

---

### Post by r-senior on 2013-02-05
OK, I had a play with this using a little project I had sitting around. I reckon that this does the job for auto dependencies:

```
CPPFLAGS=-Wall -Wextra -pedantic -std=c++0x

OBJS=driver.o logger.o properties.o

driver: $(OBJS)
	$(CXX) $(OBJS) -o driver

-include $(OBJS:.o=.d)

%.o: %.cpp
	$(CXX) -c $*.cpp $(CPPFLAGS) -MMD -MP -o $*.o 

clean:
	rm -f driver *.o *.d 

```

Adapt to your taste obviously. It seems to work, even without that nasty sed stuff in the links I gave you. They don't mention the -MP option but it generates the dummy targets they refer to and I was able to rename a header file and have it recompile without complaint.

EDIT: you can make it even shorter with implicit rules

```
CPPFLAGS=-Wall -Wextra -pedantic -std=c++0x -MMD -MP
CC=g++

OBJS=driver.o logger.o properties.o

driver: $(OBJS)

-include $(OBJS:.o=.d)

clean:
	rm -f driver *.o *.d
```

---

### Post by letsplayfootsy on 2013-02-06
Hey r-senior,
Thanks for your help. That was some interesting reading, although at the end of the 3rd link, the dude ends up calling sed THREE TIMES(!), and that is one ugly recipe. He also ends up redirecting output to a .d file, which is what I was trying to avoid in the first place..

I guess I didn't realize the "make" way of doing this is to have a .d for each source file. 

Anyways, after mucking around a bit more (actually a lot more than I care to admit) I got it working satisfactorily... For the record, here's my makefile which is doing the job now.

```

include ../Makefile.conf

SRCS = $(wildcard *.cpp) 
OBJS = ${SRCS:.cpp=.o}
CXXFLAGS += -MMD -MP
default: $(OBJS)

-include ${OBJS:.o=.d}

clean:
   rm -f *.d *.o

```

Thanks again for your help!

---

### Post by r-senior on 2013-02-06
Thanks for asking the question! I learned some useful things. This is a nice bridge between hand-written makefiles for small projects and the full autotools approach.

I like what you did with the wildcards function and the variable append. I'll build those into some of my makefiles now.

---

