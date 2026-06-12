---
title: "PATH not visible from within makefile?"
date: 2012-08-03
forum: Programming Talk
---

### Post by eotakos on 2012-08-03
Hello everyone,

Until recently I have been counting on eclipse to produce my makefiles, and I had no complain about it. But the time has come that I switched to making my own, since some peculiarities of compiling cuda code, render the automated makefiles wanting.

The problem that I encounter is that when the compiling command is executed via the make command, the PATH is not visible, and I get 

> g++: Command not found
or
> nvcc: Command not found

whereas, if I copy-paste the command that was just executed, and I execute it directly from the shell, it executes with no problems.

any Ideas?

thanks for any answers in advance

---

### Post by dwhitney67 on 2012-08-03
Create a Makefile with the following; then run 'make'.  Please report what, if anything, is the result:
```

foo:
    @ echo $(PATH)

```
Now, as for 'g++', typically you should not have to explicitly state it within the Makefile.  You should rely on $(CXX) instead.  For example:
```

APPNAME  = myprog
SRCS     = $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)
CXXFLAGS = -Wall -std=c++0x

$(APPNAME): $(OBJS)
    $(CXX) $^ -o $@

```

---

### Post by eotakos on 2012-08-03
Hello again, and thank you for your prompt reply.I was putting together a very thorough response, when I saw my mistake.

seems that... I wasn't thinking at all , when I made a variable called PATH... (yes... I know)
evidently that one overrided the environment variable and nothing was working.

Sorry for taking your time. Have a nice day


p.s. the second piece of code you enclosed is way out of my league... could you direct me to some tutorial webpage? maybe a good guide? thanks again

---

### Post by dwhitney67 on 2012-08-03
Here's a guide:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

