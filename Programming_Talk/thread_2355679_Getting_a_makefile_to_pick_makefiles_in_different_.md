---
title: "Getting a makefile to pick makefiles in different directories with similiar names"
date: 2017-03-15
forum: Programming Talk
---

### Post by 1amanewu5er on 2017-03-15
Hello all,
I have just moved from Windows environment to Linux, and have been asked to update a project - still learning but tips would be helpful!
I have a directory structure:
RootMakefile.mk
.
.--\GUI1 (Folder)
.......|--make1.mk
.......|--config(Folder)
.......|--dataprep(Folder)
...............|---makeVar1.mk
.--\GUI2 (Folder)
   .......|--make2.mk
.......|--config(Folder)
.......|--dataprep(Folder)
...............|....makeVar2.mk.
.---\GUI(n) (Folder)
.......|--make(n).mk
.......|--config(Folder)
.......|--dataprep(Folder)
...............|....makeVar(n).mk.

makefile1.mk...makefile(n).mk are similar with just the variables within changing the paths:
$(call DEF_RULES,GUI1,nodll)
$(call INCL,dataprep)

And makeVar1.mk....makeVar(n).mk are all similar with just the variables changing the path values:
GUI1_ALL:=$(call CANONICAL_PATH,$(GUI1_CONFIG)/GUI1_generated.txt)
GUI1_GWM:=$(call CANONICAL_PATH,$(GUI1_CONFIG)/gwm.xml)
GUI1_SSH:=$(call CANONICAL_PATH,$(GUI1_CONFIG)/ssh.xml)
GUI1_SSH_SUB:=$(call CANONICAL_PATH,$(GUI1_CONFIG)/ssh_sub.xml)
GUI1_SSH_APPROACH:=$(call CANONICAL_PATH,$(GUI1_CONFIG)/ssh_approach.xml)


and the task is to move all makefiles to the root so they don't need to updated each time a new GUI is added to the project.

I changed the root makefile as following:

GUI_PATH := $(wildcard GUI*/)
TARGET_FILE := GuiDetails.rb
ACTIVE_GUIS := $(filter %, $(wildcard SMA*/$(TARGET_FILE)))
GUIS_OF_INTEREST := $(filter %, $(dir $(ACTIVE_GUIS)))
DATAPREP_FOLDER := dataprep
CONFIG_FOLDER := config
DATAPREP_PATHS := $(foreach GUIS_OF_INTEREST,$(GUIS_OF_INTEREST), $(GUIS_OF_INTEREST)$(DATAPREP_FOLDER))
CONFIG_PATHS := $(foreach GUIS_OF_INTEREST,$(GUIS_OF_INTEREST), $(GUIS_OF_INTEREST)$(CONFIG_FOLDER))

Now I seem to have all the folders that containing the Target file and so the makefile(1)...makefile(n), tried this to make sure:
test:
        $(warning The following paths have guis $(GUIS_OF_INTEREST))
    $(warning The following gui paths have dataprep $(foreach GUIS_OF_INTEREST, $(GUIS_OF_INTEREST), $(GUIS_OF_INTEREST)$(DATAPREP_FOLDER)))
    $(warning The following gui paths have config $(foreach GUIS_OF_INTEREST, $(GUIS_OF_INTEREST), $(GUIS_OF_INTEREST)$(CONFIG_FOLDER)))

Is there a way now to move the makefiles within the folders to the root, and change the path variables dynamically so the guis can be generated for all different folders from a single makefile?

This would be helpful as new GUIs are added and all the variables in the nested makefile don't have to updated with the new GUI path. The number of GUIs will increase as the project progresses.

Thanks in advance! I know this might sound really novice, but this is the first time I have had to use makefile and really would appreciate the help!

---

### Post by TheFu on 2017-03-15
TL;DR - most of the new kids are using cmake, not gmake/make these days. If you don't need to compile things, a simple script might be better. 

Use relative PATHs, not absolute paths. Avoid using wildcards except to clean up old stuff - rm *.o - type stuff.

Learn that Linux is the IDE, the entire OS is an IDE.

If you are going to be a programmer on Unix systems, you'll want some basic scripting knowledge. Text processing is Unix 101 stuff. Take a class or work through one of the free online classes. Or read a book about this. Unix Power Tools the book I learned from 20+ yrs ago. Can't think of anything in it that isn't still relevant.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) might be helpful to scratch the surface.

---

### Post by 1amanewu5er on 2017-03-15
Thanks, I realize I was too quick to ask for help! I think I am following a path to the solution, will update the answer once implemented and tested.

---

