---
title: "makefile problem (error 127)"
date: 2013-05-07
forum: Programming Talk
---

### Post by Dirich on 2013-05-07
My makefile is:

```
APP = TransportAnalysis

SRCS = \
TransportAnalysis.cpp        \
taException.cpp            \
taGenerateConfigure.cpp        \
taGenerateInput.cpp        \
taGenerateREADME.cpp        \
taReadConfigure.cpp        \
taReadInput.cpp            \
taVerify.cpp            \
taPrepareSweeps.cpp        
#taPrepareHamiltonians.cpp
#taLoops.cpp

OBJS = $(SRCS:.cpp=.o)

INCLUDES =

CXXFLAGS  = -g -Wall $(INCLUDES)
LDFLAGS =
LIBS = -lgmp -lmpfr
#LIBS    := -lm -lmpfr -lgmp -lstdc++

.PHONY : all run remake clean cleanout cleanall test
.INTERMEDIATE : $(OBJS)

all : $(APP)

# This won't work if your libraries are not in a known area.
# You would need to augment the definition of LD_LIBRARY_PATH to specify
# the locations of all libraries that cannot be referenced.
run : all
    ./$(APP)

$(APP) : $(OBJS)
    $(CXX) -o $@ $^ $(LDFLAGS) $(LIBS)

# if $(OBJS) are not .INTERMEDIATE, clean should be defined as follows:
#    $(RM) $(APP)
#    $(RM) $(OBJS)
clean :
    $(RM) $(APP)

cleanout : clean
    $(RM) Data*
    $(RM) *.csv
    $(RM) *.gnu
    $(RM) *.png
    $(RM) *.jpg

cleanall : cleanout
    $(RM) Configure.*
    $(RM) Input.*

test :
    @echo "SRCS=$(SRCS)"
```

And everything works fine with it. When I try to add a new target "remake" which should essentially execute "clean" first and then "run", I get error 127.

```

remake : clean
           run
```
I tried to switch "run" for "$(APP)" and got the same error. As far as I understand make executes the clean instruction, and then go on to execute the second (either run, whose first line is $(APP), or $(APP)). The problem, I think, is that it searches for a file named $(APP) instead of executing the target $(APP).

From a more general point of view, my real problem is that sometimes my program needs to change some macro value, which means to rewrite a certain header, and to recompile itself, but make does not care if an header has been modified, it only recompiles if a source has been. Also, I do not want to call "system()" twice from my program (C++), I would like to learn to do things more elegantly, which is why I want to create the "remake" target.

---

### Post by steeldriver on 2013-05-07
I think the problem with how you're trying to do it is that 'run' is a target, not an action - you could possibly achieve the same effect by using a recursive make

```
remake : clean
      $(MAKE) run

```

but there may be a better way using an additional phony target - I'm not a makefile expert (there are one or two on here though - so hopefully they will chime in)

I don't really understand your second question - however there's nothing to stop you having header files as well as source files as prerequisites for your build targets

---

### Post by dwhitney67 on 2013-05-07
Change your remake rule to:
```

remake : clean run

```
With your original attempt, the Makefile was attempting to run an app/script called 'run', which obviously does not exist.  Hence the error.

---

