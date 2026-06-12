---
title: "make"
date: 2012-09-23
forum: Programming Talk
---

### Post by MikeCyber on 2012-09-23
Hi
why do I get: 

Project/buildFiles/Make$ make New*t
make: Nothing to be done for `New Project'.

with the file below. 
Thanks


# I release this sample under the MIT license: free for any use, provided 
# you hold me harmless from any such use you make, and you retain my 
# copyright on the actual sources.
# Copyright 2005 Jon Watte.

# AppShared Template

APPNAME := ../../game/New Project
SOURCES := ../../../../Engine/source/main/main.cpp \

LDFLAGS := -g -m32
LDLIBS := -lstdc++
CFLAGS := -MMD -I. -Wfatal-errors -m32


CFLAGS += -DUNICODE

CFLAGS += -DTORQUE_SHARED

CFLAGS_DEBUG := $(CFLAGS) -ggdb
CFLAGS_DEBUG += -DTORQUE_DEBUG
CFLAGS_DEBUG += -DTORQUE_NET_STATS
CFLAGS_DEBUG += -DTORQUE_DEBUG_GUARD

CFLAGS += -O3

#CC := gcc
LD := gcc

APP_TARGETS += $(APPNAME)
APP_TARGETS_DEBUG += $(APPNAME)_DEBUG

OBJS_New Project := $(patsubst ../../../../Engine/source/%,Release/New Project/%.o,$(SOURCES))
OBJS_New Project += $(patsubst ../../source/%, Release/New Project/%.o,$(SOURCES))
OBJS_New Project := $(filter %.o, $(OBJS_New Project))
OBJS_New Project_DEBUG := $(patsubst ../../../../Engine/source/%,Debug/New Project/%.o,$(SOURCES))
OBJS_New Project_DEBUG += $(patsubst ../../source/%, Debug/New Project/%.o,$(SOURCES))
OBJS_New Project_DEBUG := $(filter %.o, $(OBJS_New Project_DEBUG))

# Deriving the actual prerequisite list name to use from the target 
# name in the shell command is the "secret sauce" that makes this all 
# work.
#
$(APPNAME):	$(OBJS_New Project) $(SHARED_LIB_TARGETS)
	$(LD) $(LDFLAGS) -o $@ $(OBJS_New Project) $(SHARED_LIB_TARGETS) $(LDLIBS)
   
$(APPNAME)_DEBUG:	$(OBJS_New Project_DEBUG) $(SHARED_LIB_TARGETS_DEBUG)
	$(LD) $(LDFLAGS) -o $@ $(OBJS_New Project_DEBUG) $(SHARED_LIB_TARGETS_DEBUG) $(LDLIBS)

Release/New Project/%.asm.o:	../../../../Engine/source/%.asm
	@mkdir -p $(dir $@)
	nasm -f elf $< -o $@

Release/New Project/%.o:	../../../../Engine/source/%
	@mkdir -p $(dir $@)
	$(CC) -c $(CFLAGS) $< -o $@
   
Debug/New Project/%.asm.o:	../../../../Engine/source/%.asm
	@mkdir -p $(dir $@)
	nasm -f elf $< -o $@

Debug/New Project/%.o:	../../../../Engine/source/%
	@mkdir -p $(dir $@)
	$(CC) -c $(CFLAGS_DEBUG) $< -o $@
   
release_New Project: $(APPNAME)
debug_New Project: $(APPNAME)_DEBUG

.PHONY: debug_New Project release_New Project

DEPS += $(patsubst %.o,%.d,$(OBJS_New Project))
DEPS += $(patsubst %.o,%.d,$(OBJS_New Project_DEBUG))

APPNAME :=
SOURCES :=

---

### Post by spjackson on 2012-09-23
By choosing to put a space in 'New Project' you are making a rod for your own back. Don't do this unless you really enjoy the pain. It may be possible, with the right level of quoting in the Makefile to make it work, but seriously, why would you do that?

Even if you want to inflict your space on your users, the best option would be to build NewProject, then finally rename it to 'New Project'.

---

### Post by MikeCyber on 2012-09-23
Yes true, but even after changing the same:
michael@michael-P5K-PRO:~/Downloads/GarageGames-Torque3D-9afd794/MyProjects/NewProject/buildFiles/Make$ make NewProject
make: Nothing to be done for `NewProject'.

---

### Post by spjackson on 2012-09-23
OK. Your first target is $(APPNAME), but APPNAME is now
```

APPNAME := ../../game/NewProject

``` and that isn't the same as NewProject. If you need further help, please post your updated Makefile with the necessary indents, so that it's easier to follow.

---

### Post by MikeCyber on 2012-09-24
Yes, also regenerated the makefile as below. As it's generated with php code it might have some Windows line feed etc.? After importing into Eclipse I get: 
make NewProject all 
make: *** No rule to make target `NewProject'.  Stop.

Thanks



# I release this sample under the MIT license: free for any use, provided 
# you hold me harmless from any such use you make, and you retain my 
# copyright on the actual sources.
# Copyright 2005 Jon Watte.

# AppShared Template

APPNAME := ../../game/NewProject
SOURCES := ../../../../Engine/source/main/main.cpp \

LDFLAGS := -g -m32
LDLIBS := -lstdc++
CFLAGS := -MMD -I. -Wfatal-errors -m32


CFLAGS += -DUNICODE

CFLAGS += -DTORQUE_SHARED

CFLAGS_DEBUG := $(CFLAGS) -ggdb
CFLAGS_DEBUG += -DTORQUE_DEBUG
CFLAGS_DEBUG += -DTORQUE_NET_STATS
CFLAGS_DEBUG += -DTORQUE_DEBUG_GUARD

CFLAGS += -O3

#CC := gcc
LD := gcc

APP_TARGETS += $(APPNAME)
APP_TARGETS_DEBUG += $(APPNAME)_DEBUG

OBJS_NewProject := $(patsubst ../../../../Engine/source/%,Release/NewProject/%.o,$(SOURCES))
OBJS_NewProject += $(patsubst ../../source/%, Release/NewProject/%.o,$(SOURCES))
OBJS_NewProject := $(filter %.o, $(OBJS_NewProject))
OBJS_NewProject_DEBUG := $(patsubst ../../../../Engine/source/%,Debug/NewProject/%.o,$(SOURCES))
OBJS_NewProject_DEBUG += $(patsubst ../../source/%, Debug/NewProject/%.o,$(SOURCES))
OBJS_NewProject_DEBUG := $(filter %.o, $(OBJS_NewProject_DEBUG))

# Deriving the actual prerequisite list name to use from the target 
# name in the shell command is the "secret sauce" that makes this all 
# work.
#
$(APPNAME):    $(OBJS_NewProject) $(SHARED_LIB_TARGETS)
    $(LD) $(LDFLAGS) -o $@ $(OBJS_NewProject) $(SHARED_LIB_TARGETS) $(LDLIBS)
   
$(APPNAME)_DEBUG:    $(OBJS_NewProject_DEBUG) $(SHARED_LIB_TARGETS_DEBUG)
    $(LD) $(LDFLAGS) -o $@ $(OBJS_NewProject_DEBUG) $(SHARED_LIB_TARGETS_DEBUG) $(LDLIBS)

Release/NewProject/%.asm.o:    ../../../../Engine/source/%.asm
    @mkdir -p $(dir $@)
    nasm -f elf $< -o $@

Release/NewProject/%.o:    ../../../../Engine/source/%
    @mkdir -p $(dir $@)
    $(CC) -c $(CFLAGS) $< -o $@
   
Debug/NewProject/%.asm.o:    ../../../../Engine/source/%.asm
    @mkdir -p $(dir $@)
    nasm -f elf $< -o $@

Debug/NewProject/%.o:    ../../../../Engine/source/%
    @mkdir -p $(dir $@)
    $(CC) -c $(CFLAGS_DEBUG) $< -o $@
   
release_NewProject: $(APPNAME)
debug_NewProject: $(APPNAME)_DEBUG

.PHONY: debug_NewProject release_NewProject

DEPS += $(patsubst %.o,%.d,$(OBJS_NewProject))
DEPS += $(patsubst %.o,%.d,$(OBJS_NewProject_DEBUG))

APPNAME :=
SOURCES :=

---

### Post by spjackson on 2012-09-24
> **MikeCyber said:**
> Yes, also regenerated the makefile as below. As it's generated with php code it might have some Windows line feed etc.? After importing into Eclipse I get: 
make NewProject all 
make: *** No rule to make target `NewProject'.  Stop.

It's still hard to read as you don't use CODE tags to preserve formatting. Nevertheles, you still don't have a target NewProject. You don't have a target 'all' either.
```

make ../../game/NewProject

``` This would match your rule
```

$(APPNAME):	$(OBJS_New Project) $(SHARED_LIB_TARGETS)

```
If you want a target called NewProject, then you need to add one. Perhaps something like:
```

TARGET_NAME := NewProject
.
.
.
$(TARGET_NAME):	release_NewProject

``` or
```

$(TARGET_NAME):	$(APPNAME)

``` or whatever you want that target to do.

---

