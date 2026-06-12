---
title: "Shortcut for compiling and linking"
date: 2011-08-08
forum: Programming Talk
---

### Post by ltwinner on 2011-08-08
i dont want to have to type

as -gstabs -o xyz.o xyz.s
ld -o xyz xyz.p

every single time I want to build my assembly programs. I dont really know anything about writing so scripts so Im wondering is it possible to write a script so I could just type 

./myscript xyz

and it would automatically include the commands above and generate the executable?

---

### Post by Tony Flury on 2011-08-08
Look at make files - that is exactly what they are intended to do : and you can include options, libraries etc, and make files deal automatically with inter file dependencies - so you only compile what you have changed.

---

### Post by johnl on 2011-08-08
Here's a sample makefile for you with some comments.  I hope this helps.

```

TARGET = myprogram  # this is the name your final executable

AS      = as        # assembler
ASFLAGS = -gstabs   # any arguments to pass to it

LD      = ld        # linker
LDFLAGS =           # no linker flags

SRCS = main.s       # list here any source files you have


# determine the .o files from the .s files
OBJS = $(SRCS:.s=.o) 

# the below are in the form:
#
# A: B
#	C
#
# A is the target we are trying to build
# B is a list of anything that A depends on to be built
# C is the rule for how to build A given B
#
# $(TARGET), $(LD), etc are the variables we initialized above
# $@ is a special variable which is shorthand item A
# $< gives you the first item from list B
# (there is also $^ which we didn't use which gives you ALL items from list B)


# this rule tells us how to make the final program given all the .o files
$(TARGET):  $(OBJS)
	$(LD) $(LDFLAGS) $(OBJS) -o $@

# this rule is a wildcard rule:  it tells us how to make a .o file given a
# .s file
%.o:  %.s
	$(AS) $(ASFLAGS) $< -o $@

# this rule lets you remove all the temporary objects by saying 'make clean'
clean:
	rm -f $(OBJS) $(TARGET)

```

If you save this in your project's directory as 'Makefile' or 'makefile',

You can then invoke it to build your project by saying

```

make myprogram

```

or just
```

make

```

Hope this helps.

---

### Post by ltwinner on 2011-08-08
> **johnl said:**
> Here's a sample makefile for you with some comments.  I hope this helps.

```

TARGET = myprogram  # this is the name your final executable

AS      = as        # assembler
ASFLAGS = -gstabs   # any arguments to pass to it

LD      = ld        # linker
LDFLAGS =           # no linker flags

SRCS = main.s       # list here any source files you have


# determine the .o files from the .s files
OBJS = $(SRCS:.s=.o) 

# the below are in the form:
#
# A: B
#    C
#
# A is the target we are trying to build
# B is a list of anything that A depends on to be built
# C is the rule for how to build A given B
#
# $(TARGET), $(LD), etc are the variables we initialized above
# $@ is a special variable which is shorthand item A
# $< gives you the first item from list B
# (there is also $^ which we didn't use which gives you ALL items from list B)


# this rule tells us how to make the final program given all the .o files
$(TARGET):  $(OBJS)
    $(LD) $(LDFLAGS) $(OBJS) -o $@

# this rule is a wildcard rule:  it tells us how to make a .o file given a
# .s file
%.o:  %.s
    $(AS) $(ASFLAGS) $< -o $@

# this rule lets you remove all the temporary objects by saying 'make clean'
clean:
    rm -f $(OBJS) $(TARGET)

```If you save this in your project's directory as 'Makefile' or 'makefile',

You can then invoke it to build your project by saying

```

make myprogram

```or just
```

make

```Hope this helps.

Great, that is exactly what I was looking for, cheers mate.

---

