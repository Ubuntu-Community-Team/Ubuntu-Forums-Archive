---
title: "Linux Eclipse C++ programming - darn defaults - help needed"
date: 2010-01-13
forum: Programming Talk
---

### Post by akvino on 2010-01-13
OK, tell me please where in Eclipse on linux (Running Fedora11) do I tell Eclipse how to find "using namespace std;"

I selected New Project/ C++ / and added the file numberFile.cpp to test the Eclipse.. Funny thing is - I don't have any problem  doing it from command line... 

So here is what I got and here are the errors:

#include <iostream.h>
using namespace std;

void main(){
	cout << "Hello World";

}

Here is the error:
Description	Resource	Path	Location	Type
‘::main’ must return ‘int’	numberFile.cpp	Number Files	line 4	C/C++ Problem
make: *** [numberFile.o] Error 1	Number Files		line 0	C/C++ Problem

---

### Post by Queue29 on 2010-01-13
it's:

```

**int** main()
{
   ...
   return 0;
}
 
```

---

### Post by akvino on 2010-01-13
Sure I fixed that but the problem lays in linking namespace std; 

Here is what I have now:

#include <iostream.h>
using namespace std;

int main(){
	cout << "Hello World";
	return 0;

}




and I still get:
Description	Resource	Path	Location	Type
make: *** [numberFile.o] Error 1	Number Files		line 0	C/C++ Problem




Same script from the command line works by invoking g++:
@linux2 ~]$ cat numCmdTest.cpp 
#include <iostream>
using namespace std;

int main(){
	cout << "Hello World";
	return 0;
}


See that I have <iostream> instead of <iostream.h> in eclipse....
I think I need to tell Eclipse where to find these files or something...

---

### Post by dwhitney67 on 2010-01-13
Toss out the book that you are referencing; it is ancient.

Try
```

#include <**iostream**>

using namespace std;

**int** main()
{
   cout << "Hello World." << endl;
   return 0;
}

```
The return value of 0 is not necessary; C++ defaults to returning 0.  But I show it above for 'educational' purposes.

P.S.  Make sure that your file is saved with a C++ filename extension:  .cpp, .C, .cc
Then ensure that Eclipse (what a POS!) is invoking 'g++' when it compiles/links your app.

---

### Post by akvino on 2010-01-13
> **dwhitney67 said:**
> Toss out the book that you are referencing; it is ancient.

Try
```

#include <**iostream**>

using namespace std;

**int** main()
{
   cout << "Hello World." << endl;
   return 0;
}

```
The return value of 0 is not necessary; C++ defaults to returning 0.  But I show it above for 'educational' purposes.

P.S.  Make sure that your file is saved with a C++ filename extension:  .cpp, .C, .cc
Then ensure that Eclipse (what a POS!) is invoking 'g++' when it compiles/links your app.


I am all ears for the alternative POS options...

Tell me please how do I tell Eclipse (which I realize is more complicated than it's worth) to invoke g++ when I'm doing c++.
Command line - I have no problems, but need some IDE for better project management...

---

### Post by dwhitney67 on 2010-01-13
I only used Eclipse for a project I supported last year, and only then, for a brief period.

When I became more comfortable with the project, I developed my own Makefiles to build the source code, thus divorcing myself once and for all from Eclipse.  The other folks on the project continued to use Eclipse.

Anyhow, from what I can remember, there is a section of options (associated with the particular project) where you can configure the compiler to use; for some projects, plain ol' 'g++' is used, in other projects it could be a compiler for a non-native system.

As for my current assignment, I am content to say that I use 'vim' and the command line for all development tasks.

> **akvino said:**
> ...but need some IDE for better project management...
This is a myth.  Project mgmt begins with people, not the tools.

---

### Post by akvino on 2010-01-14
> **dwhitney67 said:**
> I only used Eclipse for a project I supported last year, and only then, for a brief period.

When I became more comfortable with the project, I developed my own Makefiles to build the source code, thus divorcing myself once and for all from Eclipse.  The other folks on the project continued to use Eclipse.

Anyhow, from what I can remember, there is a section of options (associated with the particular project) where you can configure the compiler to use; for some projects, plain ol' 'g++' is used, in other projects it could be a compiler for a non-native system.

As for my current assignment, I am content to say that I use 'vim' and the command line for all development tasks.


This is a myth.  Project mgmt begins with people, not the tools.


I got Eclipse to work...

Where is $OBJS defined, where is $uSER_OBJS defined, I don't get makefile..
I understand linkers but what does makefile do? This is my makefile:


# Add inputs and outputs from these tool invocations to the build variables 

# All Target
all: numbers

# Tool invocations
numbers: $(OBJS) $(USER_OBJS)
	@echo 'Building target: $@'
	@echo 'Invoking: GCC C++ Linker'
	g++  -o"numbers" $(OBJS) $(USER_OBJS) $(LIBS)
	@echo 'Finished building target: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) $(OBJS)$(C++_DEPS)$(C_DEPS)$(CC_DEPS)$(CPP_DEPS)$(EXECUTABLES)$(CXX_DEPS)$(C_UPPER_DEPS) numbers
	-@echo ' '

.PHONY: all clean dependents
.SECONDARY:

-include ../makefile.targets

---

### Post by akvino on 2010-01-14
bump

---

### Post by dwhitney67 on 2010-01-14
> **akvino said:**
> bump

What does this file contain?
```

../makefile.targets

```
OBJS is the list of your object files, which is generally put together by examining the names of your source files.  For example, and this may not exactly apply to your Makefile (in fact, I know it doesn't), but if you have a file called HelloWorld.cpp, the Makefile definition for OBJS will substitute the pattern .cpp with .o.

When I put together Makefiles, my definition of OBJS is something like:
```

OBJS := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))

```
If your plan is to continue using Eclipse, then these matters are really of no consequence to you.  IDEs are great for keeping developers in the dark.

---

