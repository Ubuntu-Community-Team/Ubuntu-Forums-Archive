---
title: "Question about if statements in makefiles"
date: 2011-01-12
forum: Programming Talk
---

### Post by the_photon on 2011-01-12
Hey guys, I am currently trying to get the following code to run as a makefile:


```
#!/bin/bash

all: create_executable

create_executable: create_object
            @echo "creating PracticeMain executable"
            g++ PracticeMain.o -o PracticeMain
            @echo "successfully created PracticeMain executable"

create_object:
            @echo "checking to see if PracticeMain.cpp exists"
             if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then
                    @echo "did not find PracticeMain.cpp"
                     else
                           @echo "found PracticeMain.cpp"
                           g++ -c PracticeMain.cpp
                           @echo "successfully created PracticeMain.o"
             fi
    
clean:
             @echo "removing PracticeMain.o"
             rm PracticeMain.o
             @echo "successfully removed PracticeMain.o"
```When I run this makefile, I get the error:
if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then
/bin/sh: Syntax error: end of file unexpected
make: *** [create_object] Error 2

I have played and played around with the various indentation possibilities, and different positionings of the "then" statement -- all to no avail.  I am down to the point now of trying random combinations of indentations, just to see if I can find one that works.

So, can anyone see anything real obvious about this?

I have checked the man files about if statements, my ubuntu programming book, and various other sources around the internet, and I really cannot see any reason why the above code does not compile when I save it and type "make" at the command prompt.

the_photon

---

### Post by Arndt on 2011-01-12
> **the_photon said:**
> Hey guys, I am currently trying to get the following code to run as a makefile:


```
#!/bin/bash

all: create_executable

create_executable: create_object
            @echo "creating PracticeMain executable"
            g++ PracticeMain.o -o PracticeMain
            @echo "successfully created PracticeMain executable"

create_object:
            @echo "checking to see if PracticeMain.cpp exists"
             if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then
                    @echo "did not find PracticeMain.cpp"
                     else
                           @echo "found PracticeMain.cpp"
                           g++ -c PracticeMain.cpp
                           @echo "successfully created PracticeMain.o"
             fi
    
clean:
             @echo "removing PracticeMain.o"
             rm PracticeMain.o
             @echo "successfully removed PracticeMain.o"
```When I run this makefile, I get the error:
if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then
/bin/sh: Syntax error: end of file unexpected
make: *** [create_object] Error 2

I have played and played around with the various indentation possibilities, and different positionings of the "then" statement -- all to no avail.  I am down to the point now of trying random combinations of indentations, just to see if I can find one that works.

So, can anyone see anything real obvious about this?

I have checked the man files about if statements, my ubuntu programming book, and various other sources around the internet, and I really cannot see any reason why the above code does not compile when I save it and type "make" at the command prompt.

the_photon

'make' needs to see it as one line, so insert \ characters at the end of the lines in the shell command.

---

### Post by the_photon on 2011-01-12
Arndt,

I appreciate the quick response, but I'm not quite sure what you mean when you say:

"make needs to see it as one line, so insert \ at the end of the shell command"

Is there any chance you (or anyone) could go into more detail about what you mean?

---

### Post by Arndt on 2011-01-12
> **the_photon said:**
> Arndt,

I appreciate the quick response, but I'm not quite sure what you mean when you say:

"make needs to see it as one line, so insert \ at the end of the shell command"

Is there any chance you (or anyone) could go into more detail about what you mean?

I meant something like this (I haven't tested it):

```
create_object:
            @echo "checking to see if PracticeMain.cpp exists"
             @if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then \
                    echo "did not find PracticeMain.cpp" \
                     else \
                           echo "found PracticeMain.cpp" \
                           g++ -c PracticeMain.cpp \
                           echo "successfully created PracticeMain.o" \
             fi
```

---

### Post by dwhitney67 on 2011-01-12
@ the_photon,

There are times when embedding shell-script within a Makefile is necessary; however in the case you presented, it is not.

The Makefile will automatically check for the existence of any files which are needed to build the final product.  If any particular file does not exist (or cannot be created), the 'make' process will abort and a message indicating the failure will be displayed.

Here's a very basic Makefile that may give you some additional ideas:
```

APP      = myapp

SRCS     = PracticeMain.cpp
OBJS     = $(SRCS:.cpp=.o)
DEPS     = $(patsubst %.cpp,%.d,$(SRCS))

DEBUG    = -g
INCLUDES =

CXXFLAGS = $(DEBUG) $(INCLUDES) -Wall -pedantic -c
LDFLAGS  =

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

.PHONY: all clean


all: $(APP)

$(APP): $(OBJS)
        $(CXX) $^ $(LDFLAGS) -o $@

%.o: %.cpp
        $(CXX) $(CXXFLAGS) $(DEPENDS) $<

clean:
        $(RM) $(OBJS)
        $(RM) *.d

realclean: clean
        $(RM) $(APP)

ifneq "$(MAKECMDGOALS)" "realclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```

---

### Post by the_photon on 2011-01-12
After following your instructions, and inserting backslash characters in the advised places, the output after running "make" at the command prompt is:

```

checking to see if PracticeMain.cpp exists
if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then \
        @echo "did not find PracticeMain.cpp" \
        else \
            @echo "found PracticeMain.cpp" \
            g++ -c PracticeMain.cpp \
            @echo "successfully created PracticeMain.o" \
    fi
/bin/sh: Syntax error: end of file unexpected (expecting "fi")
make: *** [create_object] Error 2

```

Any suggestions?

---

### Post by Arndt on 2011-01-12
> **the_photon said:**
> After following your instructions, and inserting backslash characters in the advised places, the output after running "make" at the command prompt is:

```

checking to see if PracticeMain.cpp exists
if [ ! -d "/home/brent/Desktop/PracticeInstall/PracticeMain.cpp" ]; then \
        @echo "did not find PracticeMain.cpp" \
        else \
            @echo "found PracticeMain.cpp" \
            g++ -c PracticeMain.cpp \
            @echo "successfully created PracticeMain.o" \
    fi
/bin/sh: Syntax error: end of file unexpected (expecting "fi")
make: *** [create_object] Error 2

```

Any suggestions?

Yes, better go with dwhitney's suggestion. Maybe the shell needs ; here and there when the command is all on one line - I always need to look those things up when I have multi-line shell commands in makefiles.

But you kept the @ characters within the command - that can't work. This will be executed by the shell and not have its meaning in 'make'.

---

### Post by the_photon on 2011-01-12
@dwhitney67

I completely agree with your statement that my routine to "check-for-the-existence-of-file" is actually unneccesary.  However, for right now I am just trying to learn all the in's and out's of writing "if" statements.

Really, what I'm (ultimately) trying to do is to learn to write an if-statement that will check for the existence of a file, and search in multiple places as it searches.

My longer ranging goal is to learn to read makefiles.  Even longer still, I frequently encounter the situation where I download some piece of software (such as Tcl/Tk) and it won't install on my computer, and complains that it did not install correctly.  I am trying to learn to troubleshoot difficult-to-install software.  I figure that I can ultimately install any software if I can correctly read the makefile (of the stubborn software), correctly make any changes that are needed, so that it will install correctly on my computer.

The topic of "how to read and alter makefiles in such a way as to troubleshoot software installation difficulties" does not seem to be a well addressed topic anywhere (including the internet, and man files, etc.)

Any suggestions on a course of action?

---

### Post by dwhitney67 on 2011-01-12
Bear in mind, that if you incorporate Bash-script into your Makefile, that you should insert the following statement somewhere near the top of the Makefile:
```

SHELL = /bin/bash

```
By default, Makefile uses /bin/sh, and we all should know by now that unlike many other popular distros, with Ubuntu /bin/sh is not linked to /bin/bash.

---

### Post by dwhitney67 on 2011-01-12
See this example:
```

FILE  = PracticeMain.cpp

SHELL = /bin/bash

foo:
        @ if [ -f $(FILE) ]; then \
                echo "Hooray... I have a $(FILE) file!"; \
          else \
                echo "Damn it!  Where did I place my $(FILE)?"; \
          fi

```

---

### Post by the_photon on 2011-01-12
@dwhitney67 and everyone,

Thanks for your response.  I tried it and it works.  I suppose I'll continue teaching myself to write makefiles by expanding on your code in a variety of ways.

Two remaining questions:

1.)  Although I am a moderately experienced programmer, it is probably rather obvious by my errant makefile coding attempts that I am struggling with some of the fundamentals of how makefiles work.  I have a variety of books that cover makefile programming.  However, they seem to be content to simply list correctly written programs without saying why they did what they did, and most Internet website, etc. seem to do the same.  Do you have any suggestions about where to find well written explanations of how to use the various makefile commands, and perhaps a well written tutorial for bash scripting, etc?

2.)  Websites, books, etc. about program installation on linux and linux-family systems seem to suffer from the same problem -- ambiguously written details all while omitting rather crucial, overarching principles necessary for program installation on linux and its relatives.  Any recommended websites?

thanks.

---

### Post by dwhitney67 on 2011-01-12
For Makefile:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)


For Bash: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


P.S.  I personally have never read either of the above documents; I sometimes use them for reference.  Remember, "necessity is the mother of all invention" -- thus don't bother reading about something that you will forget tomorrow simply because you have no need to apply the extra knowledge.

---

### Post by Vox754 on 2011-01-12
> **the_photon said:**
> After following your instructions, and inserting backslash characters in the advised places, the output after running "make" at the command prompt is:

```

...
/bin/sh: Syntax error: end of file unexpected (expecting "fi")
make: *** [create_object] Error 2

```


Yes, the problem was the newlines.

Essentially, "make" expects one command in each line.
```

target : prerequisite
	command_1
	command_2
	command_3

```

If you use a backslash, you are breaking a single command in multiple lines.

This code
```

target: prerequisite
	if [ -f $(FILE) ]; then \
            echo "Hooray... I have a $(FILE) file!"; \
        else \
            echo "Damn it!  Where did I place my $(FILE)?"; \
        fi
	command_2
	command_3

```

is the same as
```

target: prerequisite
	if [ -f $(FILE) ]; then echo "Hooray... I have a $(FILE) file!"; else echo "Damn it!  Where did I place my $(FILE)?"; fi
	command_2
	command_3

```

The use of backslashes in this case is for the convenience of the people reading the Makefile, but it is perfectly legal to add arbitrary code as long as it is in one line.

Beware if you do this
```

target : prerequisite
	command_1 \
	command_2 \
	command_3

```

It's the same as
```

target : prerequisite
	command_1 	command_2 	command_3

```

By the way, this brings up an important topic. Don't try to learn "bash" while trying to learn "make", it will only complicate things. Bash is full of little quirks, like variable expansion, substitution, spaces, newlines, braces, quoting, and so on.

You should try to get a good understanding of "/bin/bash", and how it differs from the minimal Posix shell "/bin/sh", and then move to learn make.

The [Advanced Bash-Scripting guide (ABS)](http://tldp.org/LDP/abs/html/) is widely regarded as a primary source to learn bash from the Internet. If you read it, you will learn useful things for sure. However, it is quite old, and I don't think its style is good enough these days, despite the fact that it's apparently still maintained.

I would recommend a more modern guide: [http://mywiki.wooledge.org/EnglishFrontPage](http://mywiki.wooledge.org/EnglishFrontPage) which also mentions the changes in the recently released Bash 4.

But don't worry, unless you are a very hardcore hacker, or a Unix dinosaur, you don't need to learn all of bash. Essentially, you learn as you go, only taking what you need.

The [GNU Bash manual](http://www.gnu.org/software/bash/manual/bashref.html) gives all of the documented features of bash, but it is not a guide to learn the language itself. You should read pieces of it when needed. It is available from "man bash".

Finally, to learn "make", I have not needed any other guide but the [GNU Make manual.](http://www.gnu.org/software/make/manual/make.html) I think it's sufficiently good. Skim through it, check out the examples, and you are good to go. It's also available through "info make".

Read some Makefiles, if you find something you don't understand check the manual again. Eventually the combination of experience with the terminal and bash, and repeated reads of the make manual, will clear most of your doubts regarding Makefiles.

---

