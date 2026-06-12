---
title: "Question about a makefile"
date: 2010-10-07
forum: Programming Talk
---

### Post by axel206 on 2010-10-07
I am trying to modify a makefile which currently is like this:

target: file1
some commands

When I type make the makefile checks the timestamp of file1 and if it is newer than the target it executes the commands.

What I want to do is to execute a few shell commands first which will update file1 or leave it the same. If file1 is updated and only then I want to run the commands of target1. Something like this:

target2:
if condition then touch file1

target1: file1
some commands

I've played with target dependencies, phony targets but I either end up with infinite loop in the makefile or I can't execute the commands of target2 before those of target1.

I don't know if I was clear enough... Does anyone have any solution?

---

### Post by Diametric on 2010-10-07
I don't have a solution, but I'm damn interested in hearing what others will say.  I'm going through a bash book and lessons right now and I'd love to hear a full explanation.  Good question.
 
Cheers.

---

### Post by dwhitney67 on 2010-10-07
When building dependencies such as this into Makefiles, one solution is leave behind a "bread crumb" indicating that a particular stage is done.

For example:
```

FILE  = file.foo
SHELL = /bin/bash

.PHONY: all

all: target2 target1

target1: $(FILE)
        @echo Doing something with $^
        @touch $@

target2:
        @[ -f $(FILE) ] || touch $(FILE)

```

---

### Post by axel206 on 2010-10-08
Thank you for the reply dwhitney67. :)

---

### Post by axel206 on 2010-10-08
One more question.. I have a makefile like this:


```
ALL_FILES = $(DIR)*.txt

target: $(ALL_FILES)
        command -o $@
```

If I run make the makefile checks all the txt files in $(DIR) and if it finds a file with timestamp newer than target it executes the command. If I add a new txt file in $(DIR) make runs the command and does the compile. However if I remove a txt file from $(DIR) there is no file with timestamp newer than target and therefore make won't do the compile. Is there a way to make it run when I delete a txt file from $(DIR)?

---

### Post by Compyx on 2010-10-08
The brute-force solution is to issue:
```
make -B
```
This will rebuild all targets, regardless of timestamps.

Ofcourse, this will get very annoying/timeconsuming when working on large projects, so a conditional would probably be better. I have little experience with conditionals in Makefiles, so I'll leave that to someone else to answer.

---

### Post by axel206 on 2010-10-08
> **Compyx said:**
> The brute-force solution is to issue:
```
make -B
```
This will rebuild all targets, regardless of timestamps.

Ofcourse, this will get very annoying/timeconsuming when working on large projects, so a conditional would probably be better. I have little experience with conditionals in Makefiles, so I'll leave that to someone else to answer.

This is a really big project and there is no way I would want to have it recompile each time. Thanks for the reply though.

---

