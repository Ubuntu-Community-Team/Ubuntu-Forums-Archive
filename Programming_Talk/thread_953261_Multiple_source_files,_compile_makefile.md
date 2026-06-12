---
title: "Multiple source files, compile makefile"
date: 2008-10-20
forum: Programming Talk
---

### Post by linuxnovice on 2008-10-20
Hi,

I am fairly new to programming in linux. For my current project, I have two .cc source files and one .h header file. I have a makefile that I am using to compile everything. 

The source files are project.cc, inputMap.cc and the header file is header.h. The header file includes all the headers needed for the project and also function declarations for the functions in both the files. project.cc contains the main() function and inputMap.cc contains only one function void inputMap(int output) for which I have declaration in header.h.

I am using the following makefile to compile my code:
CC=g++
INCLUDES=/usr/include/player-2.0
ARGS=/usr/share/player/examples/libplayerc++
LIBS=/usr/lib/libplayerc++.so.2
CFLAGS=-g -Wall -I$(INCLUDES) -I$(ARGS)
EXECUTABLES=project

all: $(EXECUTABLES)

clean:
	rm -f core $(EXECUTABLES) *.o

.SUFFIXES: .cc .o

.cc.o:
	$(CC) $(CFLAGS) -c *.cc

project: project.o inputMap.o
	$(CC) -o project project.o $(LIBS)

inputMap: inputMap
	$(CC) -o inputMap inputMap.o 

Now when I call inputMap from my project.cc file in the main() function, I get an error for undefined reference. But I am including the header file header.h which has the function declaration for inputMap. header.h is: 

#ifndef HEADER_H
#define HEADER_H

#include <libplayerc++/playerc++.h>
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <cmath>
#include <unistd.h>
#include <fstream>
#include <string>
#include "args.h"

const double pi = 3.14159265;

using namespace PlayerCc;
using namespace std;

void inputMap(int output);
#endif 

Furthermore, I am sure whether inputMap is a dependency for project.cc or not. I just call upon a function from inputMap.cc..does that make it a dependency. I am finding it hard to understand how to compile all this together. Any help is appreciated.

Thanks.

---

### Post by WW on 2008-10-20
It looks like you are missing inputMap.o in the linking command here:
```

project: project.o inputMap.o
	$(CC) -o project project.o $(LIBS)

```
Change that to
```

project: project.o inputMap.o
	$(CC) -o project project.o inputMap.o $(LIBS)

```
> 
Now when I call inputMap from my project.cc file in the main() function, I get an error for undefined reference. 

If the above suggestion doesn't fix the problem, be sure to show us the actual error message that you get.


EDIT 2:
I didn't look at the Makefile close enough the first time.  This part
```

inputMap: inputMap
$(CC) -o inputMap inputMap.o 

```
doesn't make sense.


EDIT 1:

P.S. I notice that you include the system header cmath.  cmath defines M_PI, the value of pi, so you could change this
```

const double pi = 3.14159265;

```
to
```

const double pi = M_PI;

```
or just use M_PI instead of your constant pi.

---

### Post by linuxnovice on 2008-10-20
Hi,
Thanks for your reply.

> If the above suggestion doesn't fix the problem, be sure to show us the actual error message that you get.

Here are the error messages:
```

g++ -g -Wall -I/usr/include/player-2.0 -I/usr/share/player/examples/libplayerc++ -c *.cc
g++ -o project project.o inputMap.o /usr/lib/libplayerc++.so.2
inputMap.o:/usr/include/c++/4.2/bits/stl_algobase.h:182: multiple definition of `gHostname'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2560: first defined here
inputMap.o: In function `print_usage(int, char**)':
/usr/share/player/examples/libplayerc++/args.h:59: multiple definition of `print_usage(int, char**)'
project.o:/usr/share/player/examples/libplayerc++/args.h:59: first defined here
inputMap.o: In function `parse_args(int, char**)':
/usr/share/player/examples/libplayerc++/args.h:15: multiple definition of `parse_args(int, char**)'
project.o:/usr/share/player/examples/libplayerc++/args.h:15: first defined here
inputMap.o:(.data+0x0): multiple definition of `gPort'
project.o:(.data+0x0): first defined here
inputMap.o:/usr/include/c++/4.2/bits/stl_algobase.h:182: multiple definition of `gIndex'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2560: first defined here
inputMap.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: multiple definition of `gDebug'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: first defined here
inputMap.o:(.data+0x4): multiple definition of `gFrequency'
project.o:(.data+0x4): first defined here
inputMap.o:(.data+0x8): multiple definition of `gDataMode'
project.o:(.data+0x8): first defined here
inputMap.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: multiple definition of `gUseLaser'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: first defined here
collect2: ld returned 1 exit status
make: *** [project] Error 1


```
> I didn't look at the Makefile close enough the first time.  This part
```

inputMap: inputMap
$(CC) -o inputMap inputMap.o 

```
doesn't make sense.


That part is for compiling inputMap.cc. I just extended the commands of project to inputMap. I didnt really think it through. So if I dont need that, how do I get inputMap.o without compiling it?

Thanks for the info on pi!

---

### Post by WW on 2008-10-20
> **linuxnovice said:**
> 
That part is for compiling inputMap.cc. I just extended the commands of project to inputMap. I didnt really think it through. So if I dont need that, how do I get inputMap.o without compiling it?

You are using the implicit rule for compiling .cc files into .o files.  I'm a bit rusty on the syntax, but assuming you have that set up correctly, you don't need an explicit command to compile inputMap.c.  What you have now has two problems: (1) you are saying that the file inputMap depends on the file inputMap,which doesn't make sense, and (2) the command is going to try to build an executable called inputMap from inputMap.o, which won't work because there is no main function in inputMap.c.  Try removing those two lines completely.

However, I don't think that is the source of your errors.  It is difficult to say what is causing your errors without seeing the code.  These two lines
```

inputMap.o:/usr/include/c++/4.2/bits/stl_algobase.h:182: multiple definition of `gHostname'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2560: first defined here

``` 
say that something called "gHostname" is being defined in both inputMap.c and project.c, apparently because of two different header files that have been included.

---

### Post by geirha on 2008-10-20
LIBS contain the path to a shared library, that won't work. Rather make a LDFLAGS variable that uses the -l option to link the shared library properly. (This is probably the reason for the errors you got when linking)

Also, ARGS is pointing to a set of examples that happens to contain a header file. Put that header file along with your code instead, and remove the ARGS variable.

This should be sufficient for the first part.
```

CC=g++
LDFLAGS=-lplayerc++
CFLAGS=-g -Wall -I/usr/include/player-2.0
EXECUTABLES=project

all: $(EXECUTABLES)

clean:
	rm -f core $(EXECUTABLES) *.o

.SUFFIXES: .cc .o

```


```

.cc.o:
	$(CC) $(CFLAGS) -c *.cc

```
This will compile all .cc files even if you only need to compile one. Use the special $@ and $< to represent the object file and source file respectively.
```

.cc.o:
	$(CC) $(CFLAGS) -c -o $@ $<

```

As mentioned before, the inputMap target is unnecessary, and the project target needs to be changed to use the LDFLAGS instead of LIBS:

```

project: project.o inputMap.o
	$(CC) $(LDFLAGS) -o $@ project.o inputMap.o 

```

---

### Post by linuxnovice on 2008-10-20
Hi,

Thanks for the reply guys.

I have made the changes that you suggested but I am still getting same error when I run make. I am attaching the code as text files to this reply. I did not write inputMap.cc..it was given to us as part of our project source. 

I need some help understanding stuff that you guys have suggested.

First,
> You are using the implicit rule for compiling .cc files into .o files. I'm a bit rusty on the syntax, but assuming you have that set up correctly, you don't need an explicit command to compile inputMap.c. What you have now has two problems: (1) you are saying that the file inputMap depends on the file inputMap,which doesn't make sense, and (2) the command is going to try to build an executable called inputMap from inputMap.o, which won't work because there is no main function in inputMap.c. Try removing those two lines completely.


I am assuming that implicit rule means basically since I need inputMap.o for project and I have inputMap.cc in the directory, make will automatically find it and compile it. Is that correct?

Second,
> Rather make a LDFLAGS variable that uses the -l option to link the shared library properly. (This is probably the reason for the errors you got when linking)


What are LDFLAGS? I have not worked with makefiles before, so this is pretty new to me. I have googled for tutorials but they dont explain the meaning of the flags. 

Third,
> As mentioned before, the inputMap target is unnecessary, and the project target needs to be changed to use the LDFLAGS instead of LIBS:

I made that change..but I have no idea what that means. Could someone please explain that to me. 

Finally, here are my current makefile and header.h:

```
CC=g++
LDFLAGS=-lplayerc++
CFLAGS=-g -Wall -I/usr/include/player-2.0 
EXECUTABLES=project

all: $(EXECUTABLES)

clean:
	rm -f core $(EXECUTABLES) *.o

.SUFFIXES: .cc .o

.cc.o:
	$(CC) $(CFLAGS) -c -o $@ $<

project: project.o inputMap.o
	$(CC) $(LDFLAGS) -o $@ project.o inputMap.o 
```

```
#ifndef HEADER_H
#define HEADER_H

#include <libplayerc++/playerc++.h>
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <cmath>
#include <unistd.h>
#include <fstream>
#include <string>
#include </usr/share/player/examples/libplayerc++/args.h>

const double pi = M_PI;

using namespace PlayerCc;
using namespace std;

void inputMap(int output);
#endif 

```

Here is the error I am getting right now:

```
g++ -g -Wall -I/usr/include/player-2.0  -c -o project.o project.cc
g++ -g -Wall -I/usr/include/player-2.0  -c -o inputMap.o inputMap.cc
g++ -lplayerc++ -o project project.o inputMap.o
inputMap.o:/usr/include/c++/4.2/bits/stl_algobase.h:182: multiple definition of `gHostname'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2560: first defined here
inputMap.o: In function `print_usage(int, char**)':
/usr/share/player/examples/libplayerc++/args.h:59: multiple definition of `print_usage(int, char**)'
project.o:/usr/share/player/examples/libplayerc++/args.h:59: first defined here
inputMap.o: In function `parse_args(int, char**)':
/usr/share/player/examples/libplayerc++/args.h:15: multiple definition of `parse_args(int, char**)'
project.o:/usr/share/player/examples/libplayerc++/args.h:15: first defined here
inputMap.o:(.data+0x0): multiple definition of `gPort'
project.o:(.data+0x0): first defined here
inputMap.o:/usr/include/c++/4.2/bits/stl_algobase.h:182: multiple definition of `gIndex'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2560: first defined here
inputMap.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: multiple definition of `gDebug'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: first defined here
inputMap.o:(.data+0x4): multiple definition of `gFrequency'
project.o:(.data+0x4): first defined here
inputMap.o:(.data+0x8): multiple definition of `gDataMode'
project.o:(.data+0x8): first defined here
inputMap.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: multiple definition of `gUseLaser'
project.o:/usr/include/c++/4.2/bits/locale_facets.tcc:2562: first defined here
collect2: ld returned 1 exit status
make: *** [project] Error 1
```

Thanks.

---

### Post by geirha on 2008-10-20
LDFLAGS is a commonly used variable name to put linker flags in, as CFLAGS is for compilation flags.

I had a look at args.h, and it's not a "regular" header file. It's not intended to be included from several modules. I suggest you copy the code you require from it into project.cc or create a seperate cc-file for that code.

---

### Post by linuxnovice on 2008-10-20
Hi,

I finally got it to compile. I really dont have an idea what made it to work. But the current project.cc, input.cc, header.h and makefile are attached as text files into this reply. 

The change I did was basically instead of including args.h in header.h, I included it only in project.cc. Secondly, inputMap.cc did not require stuff that was in header.h so I did not include it there and only included whatever that was needed by inputMap.cc (iostream, fstream, string etc). And now it compiled properly. 

I have some questions. I have another file called lasernoise.cpp (it was named lasernoise.cc, I changed it to lasernoise.cpp). 

First, what is a *.cc file....I see it a lot in unix systems but I dont know what it is. I know cpp is c++ file and .c is a C file. 

Second, suppose I wanted to use the function defined in lasernoise.cpp (or lasernoise.cc) in my project.cc file. What changes do I need to do in my makefile in order to do this? Furthermore, do I need to declare a function prototype of the lasernoise.cpp function in my header.h?

Thanks.

---

### Post by geirha on 2008-10-20
Both the two cc-files included header.h which in turn included args.h, so that was indeed the reason since args.h mostly contains code that should be in .cc-/.cpp-files. I still think you should avoid including the args.h file from /usr/share/wherever, and rather put it in a .cc-file.

1. .cc and .cpp are both c++ source files. .cpp is the more commonly used file extension, but they are otherwise equal.

2. Put the the prototypes in either header.h or a new header file, and make both project.cc and lasernoice.cc include that header. In the makefile, you just add lasernoice.o to the lists of .o-files (the project-line and the one below)

I can give you a quick overview of what happens with make: 

When you run make with no arguments, it will read Makefile and look for the **all** target. The **all** target in your case doesn't do anything, but it depends on **project**, so it must fulfil that dependency.

The **project** target depends on the two (soon to be three) .o-files which must be fulfilled before it can run the commands for project.

The special **.cc.o** target matches a .o-file if there exist a .cc-file by the same name. So for each .o-file it will do "g++ $(CFLAGS) -c -o <filename.o> <filename.cc>" if the .cc-file is newer than the .o-file. Thus, if you do a change only in project.cc, it will only compile that file next time your run make.

Once that is done the dependencies for the **project** target is fulfilled, and it can run the linking command.

Lastly it returns to the **all** target, which it can now run, but there is nothing to do, so make exits.

---

### Post by linuxnovice on 2008-10-20
I think I understand. Basically, headers shouldnt contain code that do stuff right? I mean headers are only for including header file, declaring functions, global variables etc. But args.h actually has a couple of functions which run loops and print out stuff. So it would not typically be a "header file" right?

Suppose, I create a source args.cc and put the code in args.h into args.cc. I then add args.o as one of the dependency for target. This should work right, because args.cc would be treated as a source and compiled like another file instead of being treated as a header.

Finally, in the dependency for project, I do not include header.h. In some makefile examples I have seen them include headers as part of the prequisite as well. Is that ok? or should I include header.h as a prequisite for project?

Thanks.

---

### Post by geirha on 2008-10-20
> **linuxnovice said:**
> I think I understand. Basically, headers shouldnt contain code that do stuff right? I mean headers are only for including header file, declaring functions, global variables etc. But args.h actually has a couple of functions which run loops and print out stuff. So it would not typically be a "header file" right?

It's not good practise to have functions in header files at least. 

> **linuxnovice said:**
> 
Suppose, I create a source args.cc and put the code in args.h into args.cc. I then add args.o as one of the dependency for target. This should work right, because args.cc would be treated as a source and compiled like another file instead of being treated as a header.


Yes, put the code in args.cc, the prototypes in header.h and add args.o to project.

> **linuxnovice said:**
> 
Finally, in the dependency for project, I do not include header.h. In some makefile examples I have seen them include headers as part of the prequisite as well. Is that ok? or should I include header.h as a prequisite for project?

Thanks.
With the way your Makefile is now, changing a header file will not trigger a new compile. You either have to update the timestamp on the .cc-files, or remove the .o-files that need to be recompiled if you want make to compile with the changed header file. Adding header files as dependencies will make make also check the timestamp of the header files against the .o-files to figure out if they require recompilation.

---

### Post by linuxnovice on 2008-10-20
Hi,

I made a file args.cc with the args.h code inside it. I modified the made file to reflect that:

```
CC=g++
LDFLAGS=-lplayerc++
CFLAGS=-g -Wall -I/usr/include/player-2.0/ 
EXECUTABLES=project

all: $(EXECUTABLES)

.SUFFIXES: .cc .o

.cc.o:
	$(CC) $(CFLAGS) -c -o $@ $<

project: project.o inputMap.o args.o header.h
	$(CC) $(LDFLAGS) -o $@ project.o inputMap.o args.o

clean:
	rm -f core $(EXECUTABLES) *.o

```

But it only compiles project.cc and inputMap.cc. When make reaches args, it says that it is needed for project but there is no rule for target.

---

### Post by dwhitney67 on 2008-10-20
Try this Makefile.  It has been augmented to support the collection of dependencies so that should you make a change to a file (whether it be a .cc or header file), the appropriate .cc modules will be recompiled.

I have also separated a few things (e.g. clean and distclean), used LDPATH and LIBS in lieu of LDFLAGS.  The rationale for the latter will become apparent when you deal with larger projects where there are more than one library and they exist in non-system directories.

I also removed the definition of CC... it is not required.  There are some other changes, but I will let you examine them and post back here if you have any questions.

As for your project, there are two possible outcomes:  either it will build, or it will not.  If the latter, it is because of a code deficiency or perhaps because you are lacking a library specification in LIBS.

```

# one way...
#SRCS    := $(wildcard *.cc)

# or, the more verbose way
SRCS     = project.cc inputMap.cc args.cc

DEBUG    = -g
CXXFLAGS = $(DEBUG) -Wall -pedantic
INCLUDES = -I/usr/include/player-2.0
LDPATH   =
LIBS     = -lplayerc++

EXEC     = project
DEP_FILE = .depend
OBJS     = $(SRCS:.cc=.o)

#
# You should not have to make any changes below this line!
#

.PHONY: all clean distclean


all: depend $(EXEC)

$(EXEC): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $(LDPATH) $(LIBS) $^ -o $@

.cc.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) core $(OBJS)

distclean: clean
	$(RM) $(EXEC)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(CXXFLAGS) $(INCLUDES) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by linuxnovice on 2008-10-20
Wow..thank you very much. I will try this makefile and get back. Although there are so many things that I really dont understand. I will have to do some reading. I found that GNU make's documentation is pretty liberal in their dealings..so I feel thats a good place to get all my inforamtion.

---

### Post by linuxnovice on 2008-10-20
> **dwhitney67 said:**
> Try this Makefile.  It has been augmented to support the collection of dependencies so that should you make a change to a file (whether it be a .cc or header file), the appropriate .cc modules will be recompiled.

I have also separated a few things (e.g. clean and distclean), used LDPATH and LIBS in lieu of LDFLAGS.  The rationale for the latter will become apparent when you deal with larger projects where there are more than one library and they exist in non-system directories.

I also removed the definition of CC... it is not required.  There are some other changes, but I will let you examine them and post back here if you have any questions.

As for your project, there are two possible outcomes:  either it will build, or it will not.  If the latter, it is because of a code deficiency or perhaps because you are lacking a library specification in LIBS.

```

# one way...
#SRCS    := $(wildcard *.cc)

# or, the more verbose way
SRCS     = project.cc inputMap.cc args.cc

DEBUG    = -g
CXXFLAGS = $(DEBUG) -Wall -pedantic
INCLUDES = -I/usr/include/player-2.0
LDPATH   =
LIBS     = -lplayerc++

EXEC     = project
DEP_FILE = .depend
OBJS     = $(SRCS:.cc=.o)

#
# You should not have to make any changes below this line!
#

.PHONY: all clean distclean


all: depend $(EXEC)

$(EXEC): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $(LDPATH) $(LIBS) $^ -o $@

.cc.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) core $(OBJS)

distclean: clean
	$(RM) $(EXEC)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(CXXFLAGS) $(INCLUDES) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

Ok I ran this makefile. First, this makefile gives a lot more information than the previous ones which is really nice. Is this because of the -pedantic flag?

Second, I couldnt have a seperate args.cc source. This is because I am using a lot of variables from args.h in my project.cc. So I tried declaring them as extern, but they still wouldnt work. Furthermore, these variables (like gIndex, gHostname etc) seems to be part of the class..and I dont exactly know how to get access to them in project.cc. So I just ended up including the args.h in my project.cc. 

Third, I ran this makefile and it gave me the following errors:
```
Makefile - compiling project.cc
In file included from /usr/include/player-2.0/libplayerc/playerc.h:55,
                 from /usr/include/player-2.0/libplayerc++/playerc++.h:39,
                 from /usr/share/player/examples/libplayerc++/args.h:1,
                 from project.cc:1:
/usr/include/player-2.0/libplayercore/player.h:2418: error: array bound is not an integer constant
In file included from /usr/share/player/examples/libplayerc++/args.h:1,
                 from project.cc:1:
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position2dProxy::GoTo(player_pose_t)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1591: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position2dProxy::GoTo(double, double, double)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position3dProxy::GoTo(player_pose3d_t)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1759: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position3dProxy::GoTo(double, double, double, double, double, double)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1766: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1767: error: ISO C++ forbids compound-literals
project.cc: In function ‘int main(int, char**)’:
project.cc:12: warning: unused variable ‘i’
project.cc:12: warning: unused variable ‘j’
make: *** [project.o] Error 1

```

I am completely lost here. The other makefile worked..but this makefile is looks really general and provides way more info..so I would like to get this to work. Unfortunetly, I am new to both programming in linux as well as programming using player. So, I guess I am really seeking a lot of external help.

Thanks for all the help guys!

---

### Post by dwhitney67 on 2008-10-20
I took a look at your code; you definitely have issues there.

Let's start with the fundamentals.  First, in the header.h file, and for that matter any header file, never include anything that is not required to support the header file.  Also, never specify a "using namespace" directive in a header file.

So looking at the header.h file, this is all that should be present (and personally, I would recommend that you rename the file to inputMap.h).
[php]
#ifndef HEADER_H
#define HEADER_H

void inputMap(int output);

#endif
[/php]

In inputMap.cc, the following should appear exactly as shown below:
[php]
#include "header.h"      // really would be better if inputMap.h
#include <fstream>
#include <iostream>

using namespace std;

...
[/php]

When writing C++ code, avoid writing it as if you were writing C code.  You can declare variables inside code-blocks, such as for loops and the such, and always initialize the variable to something.  For example:
[php]
for (int m = 0; m < someValue; ++m)
{
  ...
}
[/php]

Now, with respect to project.cc, you are calling parse_args() which you have not defined, much less implemented.  The declarations for the robot() and pp() functions are wrong.  In the main function, you are calling 'track'... which is not a legal statement.

Anyhow, in project.cc, let's start with the header files.  Insert the following:
[php]
#include "header.h"
#include <libplayerc++/playerc++.h>
#include <iostream>

using namespace std;

...
[/php]

Once you fix, or perhaps for now, just comment out, the other issues in project.cc, then try to build your project.  A worthy approach to building any project is to code a little, then test a little.

If you still have problems compiling, post your code, preferably in PHP tags.

---

### Post by linuxnovice on 2008-10-21
Hi,

> Let's start with the fundamentals. First, in the header.h file, and for that matter any header file, never include anything that is not required to support the header file. Also, never specify a "using namespace" directive in a header file.

I changed that.

> You can declare variables inside code-blocks, such as for loops and the such, and always initialize the variable to something.

I dont do that to avoid multiple declarations of the same variable. But I guess I could just keep track of them as well.

> Now, with respect to project.cc, you are calling parse_args() which you have not defined, much less implemented

parse_args() was predefined in args.h. However, I read the documentation and figured I really dont need it. So, I wrote my own parse_args in project.cc.

> The declarations for the robot() and pp() functions are wrong.

umm..I dont understand. Which part is wrong exactly? If you mean PlayerClient robot() and Position2dProxy pp()..I dont exactly know what is wrong here then. Because, this is how we have been doing it for so long.

>  you are calling 'track'... which is not a legal statement.

Sorry about that. I had a macro in my header.h (which I erased while posting here) that just printed out a bunch of stars..so that it would help me in debugging my code.

> If you still have problems compiling, post your code, preferably in PHP tags. 

I am not sure how to use the PHP tags.

So I made all the changes and compiled my code. Here is the makefile:

```
SRCS     = project.cc inputMap.cc

DEBUG    = -g
CXXFLAGS = $(DEBUG) -Wall -pedantic
INCLUDES = -I/usr/include/player-2.0
LDPATH   =
LIBS     = -lplayerc++

EXEC     = project
[COLOR="Red"]#DEP_FILE = .depend[/COLOR]
OBJS     = $(SRCS:.cc=.o)

#
# You should not have to make any changes below this line!
#

.PHONY: all clean distclean


[COLOR="Red"]#all: depend $(EXEC)[/COLOR]
all: $(EXEC)

$(EXEC): $(OBJS)
	@echo Makefile - linking $@
	@$(CXX) $(LDPATH) $(LIBS) $^ -o $@

.cc.o:
	@echo Makefile - compiling $<
	@$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) core $(OBJS)

distclean: clean
	$(RM) $(EXEC)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CXX) -E -MM $(CXXFLAGS) $(INCLUDES) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

Notice in the makefile that I have commented out two lines. I had to do this because, it kept asking for header.h for compiling project.cc but header.h is not there. I changed it to inputMap.h.

Here is project.cc:

```
#include "inputMap.h"
#include <cstdio>
#include <iostream>
#include <libplayerc++/playerc++.h>

using namespace PlayerCc;
using namespace std;

#define GRID_ROWS 1000 
#define GRID_COLS 1000

string  gHostname(PLAYER_HOSTNAME);
uint         gPort(PLAYER_PORTNUM);
uint         gIndex(0);
uint         gDebug(0);
uint         gFrequency(10); // Hz
uint         gDataMode(PLAYER_DATAMODE_PUSH);
bool         gUseLaser(false);

player_point_2d_t goal;
bool parse_args(int, char**);

extern float gridMap[GRID_ROWS][GRID_COLS];

int main(int argc, char** argv)
{
	if(!parse_args(argc,argv))
		exit(-1);

	inputMap(0);

	try
	{
		PlayerClient robot(gHostname, gPort);
		Position2dProxy pp(&robot, gIndex);
		Graphics2dProxy gp(&robot, 0);
		for (int i = 0; i < GRID_ROWS; i++)
			for (int j = 0; j < GRID_COLS; j++)
				cout << "gridMap[" << i << "] [" << j << "] = " << gridMap[i][j] << endl;
		return 0;
	} // try
	catch (PlayerCc::PlayerError e)
	{
		cerr << e << endl;
		return -1;
	} // catch
} // main

bool parse_args(int argc, char** argv)
{
	cout << "argc = " << argc << endl;

	for (int i = 0; i < argc; i ++)
		cout << "argv[" << i << "] = " << argv[i] << endl;

	// Check for number of command line arguments 
	if (argc != 3)
	{
		cout << "USAGE: ./srinivasan-HW4 x-pos y-pos" << endl;
		return (false);
	} // if
	else
	{
		// Check whether goal position is numeric
		if ((sscanf(argv[1], "%f", &goal.px) != 1)||(sscanf(argv[2], "%f", &goal.py) != 1))
		{
			cout << "Value entered not numeric...exiting" << endl;
			return (false);
		} // if
		else
		{
			// Check whether goal position is within range 
			if ((fabs(goal.px) >= 20)||(fabs(goal.py) >= 9))
			{
				cout << "Value entered out of range (|x-pos| < 20) (|y-pos| < 9)...exiting" << endl;
				return (false);
			} // if
			else
				return (true);
		} // else
	} // else
} // parse_args

```

Here is inputMap.h:

```
#ifndef INPUTMAP_H
#define INPUTMAP_H

void inputMap(int);
#endif 

```

Finally, here is inputMap.cc:

```
#include "inputMap.h"
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

#define SCALE_MAP 2
#define GRID_ROWS 1000 
#define GRID_COLS 1000

// You can change this to use dynamic memory, if you like.
float gridMap[GRID_ROWS][GRID_COLS];


/*************************************************************************
 *                                                                        *
 * Function inputMap converts the input map information into an           *
 * initial occupancy grid, which is stored in gridMap.                    *
 *                        
 * (Here, the "output" parameter says whether to print out the scaled     *
 *  map; output = 1 ==> yes, print;  output = 0 ==> no, don't print.)     *
 *************************************************************************/

void inputMap(int output) 
{
    int i, j, m, n;
    char inputLine1[80], nextChar;
    int width, height, maxVal;

    ifstream inFile("hospital_section.pnm");

    /* Initialize map to 0's, meaning all free space */

    for (m=0; m<GRID_ROWS; m++)
        for (n=0; n<GRID_COLS; n++)   
            gridMap[m][n] = 0.0;

    /* Read past first line */
    inFile.getline(inputLine1,80);

    /* Read in width, height, maxVal */
    inFile >> width >> height >> maxVal;
    cout << "Width = " << width << ", Height = " << height << endl;

    /* Read in map; */
    for (i=0; i<height; i++)    
        for (j=0; j<width; j++) {
	  inFile >> nextChar;
	  if (!nextChar)  
	    gridMap[i/SCALE_MAP][j/SCALE_MAP] = 1.0;
	}
    cout << "Map input complete.\n";

    if (output)  {
      ofstream outFile("scaled_hospital_section.pnm");
      outFile << inputLine1 << endl;
      outFile << width/SCALE_MAP << " " << height/SCALE_MAP << endl
	      << maxVal << endl;

      for (i=0; i<height/SCALE_MAP; i++)
	for (j=0; j<width/SCALE_MAP; j++) {
	  if (gridMap[i][j] == 1.0)
	    outFile << (char) 0;
	  else
	    outFile << (char) -1;
	}
       cout << "Scaled map output to file.\n";
    }
}

```

I am still getting the same error:

```
Makefile - compiling project.cc
In file included from /usr/include/player-2.0/libplayerc/playerc.h:55,
                 from /usr/include/player-2.0/libplayerc++/playerc++.h:39,
                 from project.cc:4:
/usr/include/player-2.0/libplayercore/player.h:2418: error: array bound is not an integer constant
In file included from project.cc:4:
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function &#8216;void PlayerCc::Position2dProxy::GoTo(player_pose_t)&#8217;:
/usr/include/player-2.0/libplayerc++/playerc++.h:1591: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function &#8216;void PlayerCc::Position2dProxy::GoTo(double, double, double)&#8217;:
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function &#8216;void PlayerCc::Position3dProxy::GoTo(player_pose3d_t)&#8217;:
/usr/include/player-2.0/libplayerc++/playerc++.h:1759: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function &#8216;void PlayerCc::Position3dProxy::GoTo(double, double, double, double, double, double)&#8217;:
/usr/include/player-2.0/libplayerc++/playerc++.h:1766: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1767: error: ISO C++ forbids compound-literals
make: *** [project.o] Error 1

```

Thanks for your help!

---

### Post by dwhitney67 on 2008-10-21
> **linuxnovice said:**
> 
...
I am not sure how to use the PHP tags.

When you post a message on the forum, look towards the upper-right of the input box... see the "php" icon?

...

> **linuxnovice said:**
> 
Notice in the makefile that I have commented out two lines. I had to do this because, it kept asking for header.h for compiling project.cc but header.h is not there. I changed it to inputMap.h.

Comment those lines back in, then run a "make distclean" (or just remove the .depend file), and try again.

...

> **linuxnovice said:**
> 
I am still getting the same error:

```
Makefile - compiling project.cc
In file included from /usr/include/player-2.0/libplayerc/playerc.h:55,
                 from /usr/include/player-2.0/libplayerc++/playerc++.h:39,
                 from project.cc:4:
/usr/include/player-2.0/libplayercore/player.h:2418: error: array bound is not an integer constant
In file included from project.cc:4:
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position2dProxy::GoTo(player_pose_t)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1591: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position2dProxy::GoTo(double, double, double)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1596: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position3dProxy::GoTo(player_pose3d_t)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1759: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h: In member function ‘void PlayerCc::Position3dProxy::GoTo(double, double, double, double, double, double)’:
/usr/include/player-2.0/libplayerc++/playerc++.h:1766: error: ISO C++ forbids compound-literals
/usr/include/player-2.0/libplayerc++/playerc++.h:1767: error: ISO C++ forbids compound-literals
make: *** [project.o] Error 1

```

Thanks for your help!

These look like errors in playerc++.h, not your code.  Is there a possibility that you need to include additional playerc++ header files?

As for your code, it is looking better... with the exception of the numerous global variables.  It would also be better if you used something other than sscanf() to read in a float (e.g. istringstream or use the C-library getopt() to parse your command line options).

P.S.  Try removing the -pedantic from the Makefile CXXFLAGS to see if that makes a difference in compiling project.cc

---

### Post by linuxnovice on 2008-10-21
Hi,

> When you post a message on the forum, look towards the upper-right of the input box... see the "php" icon?

Yes I see that. So I just wrap my code in php? 

> Comment those lines back in, then run a "make distclean" (or just remove the .depend file), and try again.

> P.S. Try removing the -pedantic from the Makefile CXXFLAGS to see if that makes a difference in compiling project.cc 

Yes that worked. Thanks. The code compiled without any errors. Could you please explain to me what happened that it compiled without errors?

> As for your code, it is looking better... with the exception of the numerous global variables. It would also be better if you used something other than sscanf() to read in a float (e.g. istringstream or use the C-library getopt() to parse your command line options).

Well, the only global variable that I have is goal but I need that to pass to parse_args() (maybe its because I am using sscanf).

Second, the reason I am using sscanf is because I need to check the type and range of the command line input, so I use the sscanf return value to do that. I dont know whether the other functions can be used to do the same thing.

Thanks for your help!

---

### Post by linuxnovice on 2008-10-21
I just checkout getopt(). It terminates with -1 as command line input. -1 could be a goal position for this project. So I would not want the program to terminate.

---

### Post by dwhitney67 on 2008-10-21
> **linuxnovice said:**
> ...
Yes I see that. So I just wrap my code in php?

Yep... highlight your code, then select the icon.  Or just manually wrap the code section in tags (similar to the ones you see when you quote me!)

> **linuxnovice said:**
> 
Yes that worked. Thanks. The code compiled without any errors. Could you please explain to me what happened that it compiled without errors?

Apparently the playerc++ code is not fully ISO-C++ compliant.  Damn those open-source developers; real slackers.  :-)

> **linuxnovice said:**
> 
Well, the only global variable that I have is goal but I need that to pass to parse_args() (maybe its because I am using sscanf).

Either pass the 'goal' as a parameter to parse_args(), or encapsulate it within a class (then pass the class as an arg to parse_args()).

> **linuxnovice said:**
> 
Second, the reason I am using sscanf is because I need to check the type and range of the command line input, so I use the sscanf return value to do that. I dont know whether the other functions can be used to do the same thing.

As stated earlier, istringstream.

[php]
#include <sstream>

...

std::istringstream iss(argv[1]);
float value = 0.0;

iss >> value;

if (!iss.fail())
{
  std::cout << "value = " << value << std::endl;
}
else
{
  std::cout << "You did not enter a float!" << std::endl;
}
...
[/php]

Using getopt() and strtod() would also be effective.

---

