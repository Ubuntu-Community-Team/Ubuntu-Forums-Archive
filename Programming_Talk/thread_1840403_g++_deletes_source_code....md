---
title: "g++ deletes source code..."
date: 2011-09-07
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-09-07
Hi everyone-I have been compiling with g++ for a while now, and I have a serious problem.

When g++ encounters errors, typically in header files and other ld-based situations, on occasion it will delete a source code file, typically containing main() and the offending function file that main() was trying to reference.

Apart from NEVER making typos, and being a perferct programmer ;) , is there any way round this?

I use:

```
g++ -o <title> <source code> <more source code> <header files>
```

or on occasion, wildcards:

```
g++ -o <title> *.cxx *.h
```

I am using Ubuntu 10.04 32-bit. I appreciate that this is a long shot, as I can't reproduce it reliably, but does anyone have any ideas?

EDIT: it doesn't 'move to trash' it <deletes> them from my harddisk-hence 'serious problem'

---

### Post by ziekfiguur on 2011-09-07
I have never heard of any such thing, and i seriously doubt that it's really g++ deleting files. There is probably something else going wrong, though i have no idea what that could be.

One thing though, if you use #include directives in your source files like you should, you don't have to specify the header files as command line arguments to g++
It's also always a good idea to use -Wall and -Werror arguments, and maybe -pedantic.

Edit:
Is it possible that when this happens you forgot to specify <title> in that case the file would be overwritten, but since compilation fails i can imagine that it gets deleted

---

### Post by WitchCraft on 2011-09-07
Are you using a makefile ?

In that case it's probably a bug in the :clean directive.

---

### Post by MG&amp;TL on 2011-09-07
Oh, thanks, I am #including stuff, so I don't need the header files.

-Wall was missed from my commands for simplicity of posting, I do usually include it. I'll try -pedantic in future.

Since my pattern is usually to type command carefully, then edit files to remove errors, then press up arrow, I doubt that it will be me missing the title...but I suppose it could be.

thanks for effort, will try all that you've suggested, if it still deletes stuff, I'll repost. Thanks!

---

### Post by MG&amp;TL on 2011-09-07
I am (sometimes) , but there's no clean directive. :confused:

I've isolated it from the makefile by manually issuing commands, and it still kills it.

---

### Post by MG&amp;TL on 2011-09-07
Oh yeah, and on even RARER occasions, it will spit out a corrupted version known as 'mysourcefile'~ (the tilde is appended). The source file remains untouched in this case.

---

### Post by dwhitney67 on 2011-09-07
Why don't you post your Makefile?  The suspense is killing me!

---

### Post by MG&amp;TL on 2011-09-07
Because often there isn't one. This isn't an isolated incident, I'm only asking for help because it's done it multiple times.

But as requested: (sample code-I have absolutely no idea if this will cause a problem or not, but there you go)

```
all:hello

hello: Main.cxx Hello.cxx Hello.h
[TAB]   g++ -o Hello -Wall Main.cxx Hello.cxx Hello.h


```

Although I now know that I don't need to include header files in my compilation commands.

---

### Post by ziekfiguur on 2011-09-07
> **MG&TL said:**
> Oh yeah, and on even RARER occasions, it will spit out a corrupted version known as 'mysourcefile'~ (the tilde is appended). The source file remains untouched in this case.

This is not done by g++, some editors save a backup of files you edit like that (the same filename but with a tilde).

---

### Post by SledgeHammer_999 on 2011-09-07
Or your gcc has a serious bug regression.

---

### Post by MG&amp;TL on 2011-09-07
I doubt it, I just reinstalled it when this started happening.

Anyway. I shall do as suggested and re-post should it happen again. is there a 'really verbose' mode of g++ that tells you what it's doing and why?

---

### Post by ziekfiguur on 2011-09-07
> **MG&TL said:**
> Anyway. I shall do as suggested and re-post should it happen again. is there a 'really verbose' mode of g++ that tells you what it's doing and why?

with -v it will show all the commands that are run. But it won't tell you why, as far as i know that is not possible.

---

### Post by JupiterV2 on 2011-09-07
Have you done any searches for this problem? I have never heard of this happening before nor have I ever experienced this myself with g++ nor any other GCC tool I've used. As others keep suggesting, it seems like there is something else going on. Perhaps there's a step you're not telling us? Show us an example source file, a step by step process to repeat the error, and the version of g++ you're using. Outside of that I'm not sure what can be done to help you.

---

### Post by MG&amp;TL on 2011-09-07
OK, I shall do that when I compile for first time then. Thanks for help guys!

---

### Post by MG&amp;TL on 2011-09-07
It IS a long shot, as I genuinely can't repeat it at the mo. Sorry.

Maybe I should have made that more clear

I have done some searches, and mostly things where people had made it so that the executable wrote over the source file. I'm not putting gcc down, it's a wonderful tool.

---

### Post by nvteighen on 2011-09-07
This happens quite often: using the -o flag but failing to write the output file's name, so that the first source file listed becomes overwritten by the binary. I can't tell how many times this has happened to me when compiling too quickly without much attention.

Check your ~/.bash_history file. I'm sure you'll find that this was the issue.

---

### Post by dwhitney67 on 2011-09-07
> **nvteighen said:**
> This happens quite often: using the -o flag but failing to write the output file's name, so that the first source file listed becomes overwritten by the binary. I can't tell how many times this has happened to me when compiling too quickly without much attention.


I rarely ever use the -o option, unless it is specified in a Makefile.  From the command line, I'm happy to run my application as ./a.out.

P.S.  If you require an executable with a name other than a.out, then use the 'make' utility:
```

make SomeFile   # where you have SomeFile.cpp

```

---

### Post by MG&amp;TL on 2011-09-07
Oh wow, I didn't know the bash history existed! Thanks! No, it wasn't me not specifying a name. IDK. As I say, if I can reliably reproduce it, I'll repost?

Oh yeah, and how do you use the make function? I get the GNU make error message when I use that.

---

### Post by OlyPerson on 2011-09-07
> **MG&TL said:**
> Oh yeah, and how do you use the make function? I get the GNU make error message when I use that.

Do you have a Makefile?

---

### Post by MG&amp;TL on 2011-09-07
Nope. I assumed he was talking about something different. I know how to use a makefile.

---

### Post by OlyPerson on 2011-09-07
Oh, my mistake!  As far as I know that's the only use make is for- being paired with a Makefile.

---

### Post by MG&amp;TL on 2011-09-07
That's what I thought. But I kowtow to authority.

Maybe he means put the rename commands in the makefile?

---

### Post by Arndt on 2011-09-08
> **OlyPerson said:**
> Oh, my mistake!  As far as I know that's the only use make is for- being paired with a Makefile.

No, there are implicit rules in 'make'. For simple tasks, they are enough, for example to produce MyProgram from MyProgram.cc.

---

### Post by slavik on 2011-09-08
> **MG&TL said:**
> Because often there isn't one. This isn't an isolated incident, I'm only asking for help because it's done it multiple times.

But as requested: (sample code-I have absolutely no idea if this will cause a problem or not, but there you go)

```
all:hello

hello: Main.cxx Hello.cxx Hello.h
[TAB]   g++ -o Hello -Wall Main.cxx Hello.cxx Hello.h


```

Although I now know that I don't need to include header files in my compilation commands.
hello != Hello

---

### Post by MG&amp;TL on 2011-09-08
I know that Unix/Linux filenames are case-sensitive?

Sorry slavik, I don't see what you're on about. Enlighten me?

---

### Post by JupiterV2 on 2011-09-08
He means that the make target is hello (with lower case h) and the target binary is Hello (upper case H) and that's a problem.

---

### Post by MG&amp;TL on 2011-09-08
Oh, thanks, missed it. That's just something I made up. Nice catch, slavik!

I haven't had nother problem since removing header files from compilation, so I'll mark thread <solved>. Thanks, guys!

---

### Post by dwhitney67 on 2011-09-08
> **JupiterV2 said:**
> He means that the make target is hello (with lower case h) and the target binary is Hello (upper case H) and that's a problem.

It's not a real problem.  The OP can call the resulting executable anything he pleases.

---

### Post by karlson on 2011-09-08
> **MG&TL said:**
> Because often there isn't one. This isn't an isolated incident, I'm only asking for help because it's done it multiple times.

But as requested: (sample code-I have absolutely no idea if this will cause a problem or not, but there you go)

```
all:hello

hello: Main.cxx Hello.cxx Hello.h
[TAB]   g++ -o Hello -Wall Main.cxx Hello.cxx Hello.h


```

Although I now know that I don't need to include header files in my compilation commands.

I would suggest changing your makefile first to this:

```

OBJECTS=Main.o Hello.o
CXXFLAGS = -g -Wall
LDFLAGS = 

all: Hello

Hello: $(OBJECTS)
<tab>   g++ $(CXXFLAGS) $(LDFLAGS) -o $@ $^

.cxx.o:
   $(GXX) -c $(CXXFLAGS) -o $@ $<

```

See if you can replicate the problem again.

---

### Post by dwhitney67 on 2011-09-08
CXXFLAGS are not necessary when linking the object files to form the executable.

I did not mention it before, but the OP should reconsider his use of cxx as his filename extension.  The use of cpp is more widely used, and 'make' has a built-in rule that supports this.

Here's a Makefile that searches for .cxx files:
```

APP      = Hello

SRCS     = $(wildcard *.cxx)
OBJS     = $(SRCS:.cxx=.o)

CXXFLAGS = -g -Wall
LDFLAGS  =

all: $(APP)

$(APP): $(OBJS)
    $(CXX) $^ $(LDFLAGS) -o $@

%.o: %.cxx
    $(CXX) $(CXXFLAGS) -c $<

```

And this Makefile which expects files with a .cpp (note that the final rule is not required):
```

APP      = Hello

SRCS     = $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -g -Wall
LDFLAGS  =

all: $(APP)

$(APP): $(OBJS)
    $(CXX) $^ $(LDFLAGS) -o $@

```


P.S.  Within another recent thread that I participated in, there was discussion that one should begin getting accustomed to defining both LDFLAGS and LIBS.  The latter is for specifying necessary -L and -l options.  I forgot what options could be associated with the LDFLAGS.

Needless to say, I'm old-school, and I personally will continue to use only the LDFLAGS, which using my way, should be specified *after* the listing of object files in the rule to link the application... not before.  Supposedly with the LDFLAGS/LIB split, LDFLAGS comes before the object file list, and the LIBS comes after.

---

### Post by MG&amp;TL on 2011-09-08
Okay. I just found at some erroneous site (which was ancient, tbf), that .cxx was 'the linux way'...

Anyway, I am now re-educated as regarding all things compilation. Thanks,guys.

---

### Post by WitchCraft on 2011-09-09
Is any of your source files called rm ?




> **nvteighen said:**
> 
This happens quite often: using the -o flag but failing to write the output file's name, so that the first source file listed becomes overwritten by the binary. I can't tell how many times this has happened to me when compiling too quickly without much attention.


:lolflag:

Funny, this has never ever happened to me.
But maybe lately, I have been using GUIs too often ;)

Anyway, as long as you don't have to setup bind with DLZ, you're fine.

---

### Post by MG&amp;TL on 2011-09-11
Nope, but I can see what you're getting at ;)

It is interesting running an executable that writes over itself, more and more of the ouput descends into binary and hexadecimal mush...:D

---

