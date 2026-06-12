---
title: "writing makefile"
date: 2012-09-03
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-03
Hey,
I'm really confused about writing a makefile. I kind of understand how it works, but every site on the internet gives me a different syntax.

Scenario : 
I have a C file which calls a function defined in another C file.So I also have a header file which declares the function.
main.c   - Main program calling the function, say fun();
header.h - Contains the header file which defines fun(). Say int fun()
fun.c    - Contains the definition of fun()

Compiling :
```
So I would compile this as
$gcc -L/home/Path_To_Library -I/home/Path_To_Include -lName_Of_Library -o FinalObjectFile main.c header.h fun.c

```

How do I write a Makefile for this
I tried several times but just keep getting confused seeing so many conventions, acronyms etc.
This is my try
```

LIB=-L/Path_To_Library
INC=-I/Path_To_Include
CC=gcc
DEPS=header.h

OBJS            = main.o fun.o
expr            : $(OBJS)
	$(CC) $(CFLAGS) -o $(.TARGET) $(.ALLSRC)
main.o          : main.c
	$(CC) $(CFLAGS) -c main.c
fun.o         : fun.c
	$(CC) $(CFLAGS) -c fun.c
$(OBJS)         : $(DEPS)

```

Please correct this, so I can get a good template to write in future.

Thanks

---

### Post by dwhitney67 on 2012-09-03
> **IAMTubby said:**
> 
Compiling :
```
So I would compile this as
$gcc -L/home/Path_To_Library -I/home/Path_To_Include -lName_Of_Library -o FinalObjectFile main.c header.h fun.c

```

For such a simple example, why are you specifying a path to a library and using a library?  And why are you specifying the header file?  Header files are included in the source file(s); they do not need to be compiled.

> **IAMTubby said:**
> 
How do I write a Makefile for this

There are many ways to setup your project directory; source code could be in different directory than header files, or they could very well be in the same place.  It is very rare that one Makefile will work for all projects.

For the simple project where the source and header files are in the same directory, the following Makefile will work:
```

EXE     = myexe

SRCS    = main.c fun.c
OBJS    = $(SRCS:.c=.o)

CFLAGS += -Wall

LDFLAGS =


$(EXE) : $(OBJS)
        $(CC) $^ $(LDFLAGS) -o $@

clean :
    $(RM) $(OBJS) $(EXE)

```
If you are using any external libraries, for example libm.so, then you would add a -lm to the LDFLAGS.


P.S.  Here's a more thorough looking Makefile, which assumes that header files reside in a subdirectory called 'Include', and that source files reside in one or more subdirectories:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.c')
SRCDIRS := $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.c,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = -I./Include
CFLAGS   = $(DEBUG) -Wall -pedantic $(INCLUDES) -c
LDFLAGS  =
LIBS     =

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
	$(CC) $(LDFLAGS) $^ $(LIBS) -o $@

$(OBJDIR)/%.o: %.c
	$(CC) $(CFLAGS) $(DEPENDS) $< -o $@

clean:
	$(RM) -r $(OBJDIR)

distclean: clean
	$(RM) $(APP)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
	mkdir -p $(OBJDIR)/$$dir; \
   done
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```

---

### Post by IAMTubby on 2012-09-03
dwhitney, thanks for the help.

> **dwhitney67 said:**
> For such a simple example, why are you specifying a path to a library and using a library?
I just want to try and understand so that I can write more complex scenarios.


> 
And why are you specifying the header file?  Header files are included in the source file(s); they do not need to be compiled.

I'm sorry, I didn't know that. But if that's the case, how do I add a library from some other path, not the current directory ?
I thought -L was used for that purpose. Please correct me. 


> 
For the simple project where the source and header files are in the same directory, the following Makefile will work:
```

EXE     = myexe

SRCS    = main.c fun.c
OBJS    = $(SRCS:.c=.o)

CFLAGS += -Wall

LDFLAGS =


$(EXE) : $(OBJS)
        $(CC) $^ $(LDFLAGS) -o $@

clean :
    $(RM) $(OBJS) $(EXE)

```
If you are using any external libraries, for example libm.so, then you would add a -lm to the LDFLAGS.

I tried compiling this using make. But it gives me an error saying "*** missing separator.  Stop."


I didn't try the other Makefile you sent me. Want to get an easy one working first.

Thanks.

---

### Post by IAMTubby on 2012-09-03
Just to add on that,
when I directly tried the example, it gave me the error
```

Makefile:12: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```

So I removed 2 spaces, and then it gives me the error
```

Makefile:12: *** missing separator.  Stop.

```

Please advise. Thanks.

---

### Post by steeldriver on 2012-09-03
Did you copy + paste dwhitney's example? or type it out yourself?

The commands in makefiles MUST be indented with a TAB - if you used spaces it will give the "missing separator" error

---

### Post by IAMTubby on 2012-09-03
I copy pasted,
Shall type it out and let you know within a couple of minutes.

But where are we accounting for the -L and -I.
I am actually running some CUnit test, and the lib and include for CUnit is in some other location.

Can you please add the template for that too in the Makefile above.
I know you have to do 
```

LIB=-L/Path...
INC=-I/Path...

```

But how do I add this to the compile line in the Makefile ?
As in, is it supposed to be like
```

%.o:%.c $(DEPS)
      $(CC) -c -o $@ $< $(LIB) $(INC)

```

Please post the entire Makefile, when you make changes to mine. I'm finding small code pieces of the Makefile difficult to integrate. Sorry first time!

---

### Post by dwhitney67 on 2012-09-03
When compiling a source file, you may need to specify the path to any header files which are not within the current directory; you use the uppercase I option for that.  The exception to this rule is the "standard" search path that GCC uses to locate header files.  (run 'gcc --print-searc-dirs' to locate standard directories).

As for libraries, their header file(s) are used in the compiling step, however the actual shared-object or static library is NOT used.  The library is only referenced when linking the one or more object files to produce an executable image of your program.

Similarly, CFLAGS, which is used for compiling source files, has no use when linking object files.

So, with this in mind, if you lay out your Makefile in an orderly fashion, it becomes quite trivial.  If you are using the CUNIT library, installed at path /home/me/cunit, then something like this could be used:
```

# Declarations section
#
APP       = mytest

SRCS      = $(wildcard *.c)
OBJS      = $(SRCS:.c=.o)

CUNIT_DIR = /home/me/cunit

INCLUDES  = $(CUNIT_DIR)/include
CFLAGS    = -Wall $(INCLUDES)

LDFLAGS   = -L$(CUNIT_DIR)/lib
LIBS      = -lcunit


# Rules section
#
$(APP) : $(OBJS)
        $(CC) $^ $(LDFLAGS) $(LIBS) -o $@

clean :
        $(RM) $(OBJS) $(APP)

```
Some developers, such as myself, often combine the LDFLAGS and LIBS into one larger statement, still calling it LDFLAGS.  You do as you please.

The 'make' command has built-in rules for compiling source files.  Generally these are sufficient, however if you require something special to be done, then you can define your own; for example.
```

%.o : %.c
        @ echo Compiling $<
        $(CC) $(CFLAGS) -c $<

```


P.S.  My examples above are written from memory; thus they have not been tested, nor did I account for placing tabs, in lieu of 8-spaces, for the statements following the rules.  I would think that you would know this basic necessity by now.

---

### Post by IAMTubby on 2012-09-03
dwhitney,
That was magical! :)
Worked perfect. I still have to google and find a few things from the makefile and get back to you if I don't get it.

Shall mark the thread as solved after some time. Is that fine ?

---

### Post by IAMTubby on 2012-09-04
Hey, I have a doubt in one of the syntax I came across.

```

LIBS = -L$(RAC_ROOT_DIR)/lib\
	 -lfirst \
	 -lsecond \
	 -lthird \
	 -lfourth 

```

I have 2 questions
1)I understand we are adding multiple library paths here ? But some confusing syntax is being used to make it shorter.
If you expand these , what do you get ?

Do you get
```

-L$(RAC_ROOT_DIR)/lib/-lfirst
-L$(RAC_ROOT_DIR)/lib/-lsecond
-L$(RAC_ROOT_DIR)/lib/-lthird
-L$(RAC_ROOT_DIR)/lib/-lfourth

```

or do you get
```

-L$(RAC_ROOT_DIR)/lib/
-L$(RAC_ROOT_DIR)/-lfirst
-L$(RAC_ROOT_DIR)/-lsecond
-L$(RAC_ROOT_DIR)/-lthird
-L$(RAC_ROOT_DIR)/-lfourth

```

2)What if I have to add an additional library at the end of this How would it look like ?
Is this correct ?

```

LIBS = -L$(RAC_ROOT_DIR)/lib\
	 -lfirst \
	 -lsecond \
	 -lthird \
	 -lfourth \
       -L/Path_To_The_Next_Library

```

3)How does a Makefile work when you are adding multiple library paths ? Does it go like this ?
```

For(SourceFile = 1 to SourceFile = Total)
{
 while(CorrectLibraryNotFound)
  Check NextLibraryPath
}

```

Thanks.

---

### Post by dwhitney67 on 2012-09-04
You're assumptions are a little off; the LIB variable is set to a single line.  The slashes are used to denote a break in the line, but nothing else.  So LIB is equivalent to:
```

LIBS = -L$(RAC_ROOT_DIR)/lib -lfirst -lsecond -lthird -lfourth

```
As for the Makefile, it does not check for the existence of libraries, unless you list them as dependencies to a particular rule.  As for LIB, only GCC knows how to process those options.

```

...

LIB = -L../lib -lsample

MYLIB = ../lib/libsample.so

# This rule is dependent on the existence of $(MYLIB)
rule1 : $(MYLIB) $(OBJS)
        $(CC) $^ -o $(MYEXE)

# This rule does not check that $(LIB) is valid; GCC does that.
rule2 : $(OBJS)
        $(CC) $^ $(LIB) -o $(MYEXE)

$(MYLIB) :
        $(MAKE) -C ../lib

```

---

### Post by IAMTubby on 2012-09-04
dwhitney,
Still finding it difficult. :(

The makefile you gave me yesterday worked fine. Now I have to add the necessary parts to an existing makefile.

I know that these are the important steps.(We are talking about CUnit)

1)Add -L
I want to add -L/home/local/lib to the existing part which looks like
```

LIBS = -L$(RAC_ROOT_DIR)/lib\
	 -lfirst \
	 -lsecond \
	 -lthird \
	 -lfourth 

```
So, I added as follows
```

LIBS = -L$(RAC_ROOT_DIR)/lib\
	 -lfirst \
	 -lsecond \
	 -lthird \
	 -lfourth 
        -L/home/local/lib

```

2)Add -I
I want to add -I/home/local/include to the existing part which 
looks like
```

INCLUDE_PATHS += -I./ \
		-DLINUX \
		-I${SOURCE_DIR} \
		-I${COMMON_DIR} \
		-I${SYSTEM_DIR} \
		-I${SYSLNX_DIR} 

```
So I added as follows
```

INCLUDE_PATHS += -I./ \
		-DLINUX \
		-I${SOURCE_DIR} \
		-I${COMMON_DIR} \
		-I${SYSTEM_DIR} \
		-I${SYSLNX_DIR}
                -I/home/local/include

``` 


3)Add -lcunit
This is fine, the syntax in the existing makefile is straight forward  

4)Adding this
```

SRCS      = $(wildcard *.c)
OBJS      = $(SRCS:.c=.o)
$(APP) : $(OBJS)
        $(CC) $^ $(LDFLAGS) $(LIBS) -o $@

```

I guess this is not necessary because the makefile already has some rules like
```

%.o: $(SOURCE_DIR)/%.c
	$(CC) -c $? $(CFLAGS)

%.o: $(COMMON_DIR)/%.c
	$(CC) -c $? $(CFLAGS) 

%.o: $(SYSTEM_DIR)/%.c
	$(CC) -c $? $(CFLAGS)  

%.o: $(SYSLINUX_DIR)/%.c
	$(CC) -c $? $(CFLAGS)

```

What am I doing wrong ?

---

### Post by dwhitney67 on 2012-09-04
> **IAMTubby said:**
> 
What am I doing wrong ?
You should add -lcunit to the end of LIBS; should look something like:
```

LIBS = -L$(RAC_ROOT_DIR)/lib\
       -lfirst \
       -lsecond \
       -lthird \
       -lfourth 
[B]       -L/home/local/lib
       -lcunit[/B]

```

Now, for your second question... I could have given you a better advice earlier if I knew that your source code resided in multiple directories.  Change SRCS to be the following:
```

SRCS = $(wildcard $(SOURCE_DIR)/*.c $(COMMON_DIR)/*.c $(SYSTEM_DIR)/*.c $(SYSLINUX_DIR)/*.c)
...

```
Alternatively, you could try something like:
```

SRCS = $(shell find . -name '*.c')
...

```

---

### Post by IAMTubby on 2012-09-04
> **dwhitney67 said:**
> You should add -lcunit to the end of LIBS; should look something like:
```

LIBS = -L$(RAC_ROOT_DIR)/lib\
       -lfirst \
       -lsecond \
       -lthird \
       -lfourth 
[B]       -L/home/local/lib
       -lcunit[/B]

```

dwhitney,
not too sure if that's working.

But the makefile already has a line 
```

LIBS += -lc -largtable2

```
So isn't it more correct to append -lcunit along with LIBS ?

> 
Now, for your second question... I could have given you a better advice earlier if I knew that your source code resided in multiple directories.  Change SRCS to be the following:
```

SRCS = $(wildcard $(SOURCE_DIR)/*.c $(COMMON_DIR)/*.c $(SYSTEM_DIR)/*.c $(SYSLINUX_DIR)/*.c)
...

```
Alternatively, you could try something like:
```

SRCS = $(shell find . -name '*.c')
...

```
I don't think I can add an SRCS part to the Makefile. Currently, there is a OBJS part which contains lot of .o files.
And at the end of all this, there are rules as follows


```

$(LIBFILE) : $(OBJS)
        $(LINK) $(LDFLAGS) \
                --retain-symbols-file,$(SYMFILE) \
                -Wl,-soname,$(LIBFILE) \
                -Wl,-Map,$(MAPFILE) \
                -o $@ \
                $(OBJS) \
                $(LIBS)


%.o: $(COMMON_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

%.o: $(STRING_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

%.o: $(SYSTEM_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

%.o: $(RACADM_SYSLNX_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

%.o: $(SYSAPI_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

%.o: $(TLOG_DIR)/%.c
        $(CC) -c $? $(CFLAGS)

```

I would have thought that I'm not doing either of -L, -l or -I correctly as mentioned in the previous mail

---

### Post by dwhitney67 on 2012-09-04
> **IAMTubby said:**
> dwhitney,
not too sure if that's working.

That's because I forgot to apply the line-continuation character.  Sorry about that.
```

LIBS = -L$(RAC_ROOT_DIR)/lib\
       -lfirst \
       -lsecond \
       -lthird \
[B]       -lfourth \
       -L/home/local/lib \
       -lcunit[/B]

```

> **IAMTubby said:**
> 
But the makefile already has a line 
```

LIBS += -lc -largtable2

```
So isn't it more correct to append -lcunit along with LIBS ?

Do what you please.  You could also just do this:
```

LIBS += -L/home/local/lib -lcunit

```
The "plus-equals" operator just appends to the end of the variable.

> **IAMTubby said:**
> 
I don't think I can add an SRCS part to the Makefile. Currently, there is a OBJS part which contains lot of .o files.

How did the list of .o files get generated?  Surely it wasn't done by hand (ie. manually).  That would be lame.

> **IAMTubby said:**
> 
And at the end of all this, there are rules as follows

The rules look fine.

---

