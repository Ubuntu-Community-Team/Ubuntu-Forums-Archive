---
title: "error compiling c code"
date: 2009-07-07
forum: Programming Talk
---

### Post by le_vainqueur on 2009-07-07
I am trying to compile c codes that I need for my research which I found here: [ftp://ftp.wiley.com/public/sci_tech_med/phase_unwrapping/](ftp://ftp.wiley.com/public/sci_tech_med/phase_unwrapping/)

After downloading and extracting the files, I navigated to that directory in a terminal and entered the following command:

> cc -c flynn.c

That seemed to work fine, so I entered the next command

> cc -o flynn flynn.c

At this point, the following came out:

> /usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/ccYYK55G.o: In function `FlynnMinDisc':
flynn.c:(.text+0x44a): undefined reference to `ChangeExten'
flynn.c:(.text+0x49f): undefined reference to `RemoveLoop'
flynn.c:(.text+0x4d8): undefined reference to `ChangeOrphan'
flynn.c:(.text+0x794): undefined reference to `ChangeExten'
flynn.c:(.text+0x7e9): undefined reference to `RemoveLoop'
flynn.c:(.text+0x822): undefined reference to `ChangeOrphan'
flynn.c:(.text+0xae0): undefined reference to `ChangeExten'
flynn.c:(.text+0xb35): undefined reference to `RemoveLoop'
flynn.c:(.text+0xb6e): undefined reference to `ChangeOrphan'
flynn.c:(.text+0xe23): undefined reference to `ChangeExten'
flynn.c:(.text+0xe78): undefined reference to `RemoveLoop'
flynn.c:(.text+0xeb1): undefined reference to `ChangeOrphan'
collect2: ld returned 1 exit status

Unfortunately, I am unable to decipher this. When I tried to enter the next command,

> ./flynn

the result was as follows

> bash: ./flynn: No such file or directory


Is there anything I can do about this?

---

### Post by Mad Hacker on 2009-07-07
what library are you using? it looks like you need to do something like this
```
cc -c flynn.c -libname
```where libname is the name of the library
although i'm not very familiar with compiling from the command line, so i could well be wrong

it might also be that you forgot to #include a file

the reason that this
```
./flynn
```does not work is that it is trying to execute the program, but as the compiler found errors it did not create an executable

---

### Post by Zugzwang on 2009-07-07
First of all, if you do not specify the "-c" option, "g++" will assume that you gave all source code files that comprise the application your are trying to compile (you can also give some .o files which are already compiled). In your case, the file your are compiling has no "main(...)" function *AND* is also incomplete, i.e. it lacks the definitions of some functions it refers to.

---

### Post by Ratscallion on 2009-07-07
Basically, finish the code up then try something along the lines of
> g++ -o (change to -c if you need) "Executable" "SOURCE FILE"

---

### Post by le_vainqueur on 2009-07-07
Thanks for the responses so far, here are my comments/questions.

> **Mad Hacker said:**
> what library are you using? it looks like you need to do something like this
```
cc -c flynn.c -libname
```where libname is the name of the library
although i'm not very familiar with compiling from the command line, so i could well be wrong

Thanks for the tip.  I don't actually know much about compiling.  My programing experience is all in MATLAB, so this is a new beast for me

> **Mad Hacker said:**
> 
it might also be that you forgot to #include a file

the reason that this
```
./flynn
```does not work is that it is trying to execute the program, but as the compiler found errors it did not create an executable

That could be, I'll have to look into it.  Wouldn't the output of the "./flynn" comman be different if that were the case, though?

> **Zugzwang said:**
> First of all, if you do not specify the "-c" option, "g++" will assume that you gave all source code files that comprise the application your are trying to compile (you can also give some .o files which are already compiled). In your case, the file your are compiling has no "main(...)" function *AND* is also incomplete, i.e. it lacks the definitions of some functions it refers to.

Should I have specified the -c option elsewhere?  I did place it in the first command, but not the second.  Is there something wrong with my approach there?

By incomplete, do you mean something like what Mad Hacker was referring to (including a file)?  

> **Ratscallion said:**
> Basically, finish the code up then try something along the lines of

I'm not sure what you mean.  The code I am trying to compile here was actually published in a book, so it should be finished.

---

### Post by dwhitney67 on 2009-07-07
@ the OP

1. Download [code.zip]("ftp://ftp.wiley.com/public/sci_tech_med/phase_unwrapping/code.zip").

2. Unzip the code.zip
```

unzip code.zip

```

3. Create a Makefile in ./phase/code/ directory
```

cd ./phase/code
gedit Makefile



# then copy/paste the following text, not including this line!

APP     = flynn

SRCS    = dxdygrad.c \
          extract.c \
          flynn.c \
          getqual.c \
          grad.c \
          histo.c \
          mainflyn.c \
          maskfat.c \
          qualgrad.c \
          qualpseu.c \
          qualvar.c \
          trees.c \
          util.c

OBJS    = $(SRCS:.c=.o)

CFLAGS  = -c
LDFLAGS = -lm

.PHONY: all clean


all: $(APP)

$(APP): $(OBJS)
        @echo Linking $@
        @$(CC) $(OBJS) $(LDFLAGS) -o $@

.c.o:
        @echo Compiling $<
        @$(CC) $(CFLAGS) $<

clean:
        $(RM) $(OBJS)
        $(RM) $(APP)

```

4.  Build, and then run, the flynn application.
```

make
./flynn

```

P.S.  Ignore the warnings when building the application; apparently the authors were not attentive when they developed the code.

P.S.S.  Btw, next time read the appropriate "main" (e.g. mainflyn.c) file for instructions on how to build the s/w.  The authors should have placed the build information inside the README.code file.

---

### Post by Simian Man on 2009-07-07
You are either missing some code (it may be in a separate file or module) or you need to link to some library.  Not all code in books can be run as is.  Often times it's listed as something to get you started or to give you an idea of what to do.

What is the program/book you are working with?

---

### Post by le_vainqueur on 2009-07-07
> **dwhitney67 said:**
> 
4.  Build, and then run, the flynn application.
```

make
./flynn

```


Thanks for the help.  I wasn't aware of the mainflynn.c file.  It definitely clears some things up.  I am not sure what you mean in step 4 of your post, however.  The "code" section of your post, primarily.  Was the method I initially used to build correct?  How does this "Makefile" come into play?  


> **Simian Man said:**
> You are either missing some code (it may be in a separate file or module) or you need to link to some library.  Not all code in books can be run as is.  Often times it's listed as something to get you started or to give you an idea of what to do.

What is the program/book you are working with?

Thanks, it appears that this was the case.  The book that I am working from is "Two-Dimensional Phase Unwrapping Theory, Algorithms, and Software" by Ghiglia.

---

### Post by dwhitney67 on 2009-07-07
Edit a new file called "Makefile".  Insert the contents that I provided in my earlier post.  Save the file.

Then, from the same directory where this Makefile resides, type the command "make".  In a few moments, your application will be built.

The alternative is to examine the list of files (either in the Makefile I provided or from within mainflyn.c), and build the application manually.
```

gcc dxdygrad.c extract.c flynn.c ... util.c -o flynn 

```
You are not missing any code.  You are just lacking the experience on how to build a software application.  Follow the instructions I have provided and you will be fine.  Deviate from them, and undoubtedly you will encounter yet another problem.

---

### Post by le_vainqueur on 2009-07-08
Thanks for the explanation on the Makefile.  It's becoming clearer.  The software is now compiling correctly! w00t!

---

### Post by dwhitney67 on 2009-07-08
> **le_vainqueur said:**
> Thanks for the explanation on the Makefile.  It's becoming clearer.  The software is now compiling correctly! w00t!

You're welcome.  Please forgive me for being a bit blunt in my previous response.

If you need to build the other applications, refer to the appropriate "main" C file to see what the dependencies are.  You can create multiple Makefiles; just ensure they have unique file names (eg. MakeFlynn).

To build a makefile that does not have a standard name, the following command option is used:
```

make -f MakeFlynn

```

---

