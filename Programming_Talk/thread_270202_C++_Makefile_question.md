---
title: "C++ Makefile question"
date: 2006-10-02
forum: Programming Talk
---

### Post by neilp85 on 2006-10-02
I'm trying to get my Makefile to easily handle a suite of test cases for a project as it grows. Is there some way to loop though each test file and create a target and rule for each of these. I've been reading through the GNU Make Manual some and couldn't find an example of how to do this. Right now I have to add a new target for every new test case that I come up with like so:
```
test1:   test1.cpp
   g++ -g -o test1 test1.cpp

test2:   test2.cpp
   g++ -g -o test2 test2.cpp

...
```
I know you I can do the following to get a list of the test files  I have created:
```
TEST_FILES := $(wildcard test*.cpp)
```
The problem is I'm not sure how to turn that list into a set of targets and rules. From what I've gathered it looks like I'll have to use some combination of the foreach and call functions but I couldn't put it all together and get it working. Anyone out there with some experience doing this?

---

### Post by po0f on 2006-10-02
neilp85,

Use this instead:
```
SOURCES=test1.cpp test2.cpp
OBJECTS=$(SOURCES:.cpp=.o)

all: $(OBJECTS)

.cpp.o:
    g++ -Wall -o $@ $<
    mv $@ $(shell basename $@ ".o")
```

All you have to do from this point is add the file that you want compiled to the SOURCES variable.

---

### Post by neilp85 on 2006-10-03
Would someone mind explaining to me exactly how the above Makefile works. Mainly how does the assignment of OBJECTS and the compile and move commands work?

---

### Post by neilp85 on 2006-10-03
Also, is there a way to get rid of having to do the move entirely? Doing this tricks make into thinking that nothing is up to date so it recompiles everything each time.

---

### Post by po0f on 2006-10-03
neilp85,

I couldn't think of an easy way to compile the object file into a file not ending in .o.  You can comment out the mv command and run the object files directly, I tested it.  Maybe you can remove the mv command entirely and do something like this:
```
.cpp.o:
    g++ -Wall -o $(shell basename $@ ".cpp") $@
```

The all rule requires OBJECTS to be up to date.  The declararion of OBJECTS pretty much means "Ok, for each source file that ends in .cpp, use the default rule for turning .cpp files into .o files".  And the way the .cpp.o rule works is whenever a .cpp file has to be compiled automatically (it's the default rule for .cpp to .o), compile the file $< that triggered the command into $@.

I'm guessing that the above fix will work, but in either case, both of my solutions are hacks.  I don't have much experience writing Makefiles.  And thinking about it, you won't have .o files with the above fix, so recompilation will happen anyway.  Just leave them as object files and run them directly, it doesn't hurt anything.  I really should read more about make...

---

### Post by neilp85 on 2006-10-03
I had actually come up with the above Makefile but had the same problem with things getting recompiled. Thanks for the input though.

---

