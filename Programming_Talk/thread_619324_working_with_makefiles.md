---
title: "working with makefiles"
date: 2007-11-21
forum: Programming Talk
---

### Post by arielsegal on 2007-11-21
In the project I'm working on, each sub-project has its own directory. There is one big and complicated makefile that builds the whole project. How can I have a separate makefiles for each sub-project, in every directory, and when changing the local makefile, I would not have to change the master makefile?

---

### Post by Compyx on 2007-11-21
Sounds like you might want to include the sub project makefiles in the project-wide makefile. Have a look at the [manual]("http://www.gnu.org/software/make/manual/html_node/Include.html#Include").

---

### Post by arielsegal on 2007-11-21
Thank you for the answer, but still I got a problem. If I maintain object file lists only in the sub-makefiles, how would the master makefile know about them, without duplicate them all in the master makefile?
Does anyone have an example of such a situation?

---

### Post by dwhitney67 on 2007-11-22
I think it is silly to organize source code into separate directories, unless of course these are used to make individual libraries or they are for supporting different architectures.  Think of the analogy of stuffing your socks into separate drawers in your dresser solely based on the color of the sock... kinda dumb.

However, if your case is one where you are creating individual libraries (or even applications), something like this could work:

Top-level Makefile:
```
DIRS = dir1 dir2 dir3

all:
        for dir in $(DIRS); do make -C $$dir $@; done

```

And a sample Makefile in one of the subdirectories:
```
LIBSRC  = src1.cpp src2.cpp src3.cpp
LIBOBJ  = $(LIBSRC:.cpp=.o)

LIB     = myLibrary.a
LIBDEST = ../

all: $(LIB)
        install -m 555 $(LIB) $(LIBDEST)
        touch $@

$(LIB): $(LIBOBJ)
        $(AR) r $(LIB) $(LIBOBJ)

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $< -o $@
```

The Makefile code shown above is merely an example; it should be usable, however I have not tested it.  Nevertheless I hope it explains the basics how to setup the Makefile hierarchy.

Btw, another trick is to maintain a list of dependencies for a source file.  If none of the dependencies have changed, and the product is up-to-date, then the source is not recompiled.

Something like this is included in the sub-dir Makefile:
```
depend:
        #-------------------
        # Makefile: $@
        #-------------------
        @$(RM) $(DEP_FILE)
        @for i in $(LIBSRC) ; do \
                $(GPP) -E -MM $$i >> $(DEP_FILE); \
        done

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring cleanall,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by seetho on 2007-11-22
> **arielsegal said:**
> Thank you for the answer, but still I got a problem. If I maintain object file lists only in the sub-makefiles, how would the master makefile know about them, without duplicate them all in the master makefile?
Does anyone have an example of such a situation?

Just keep the common stuff in a separate include file that you should include in your main make file and sub make files.  This way if you need to change anything globally you just have to modify just one file.

This concept does not only apply to makfiles but also to good programming practice in general.

st

---

### Post by arielsegal on 2007-11-22
Thank you, you really helped me very much.
dwhitney67 said:
> I think it is silly to organize source code into separate directories, unless of course these are used to make individual libraries or they are for supporting different architectures. Think of the analogy of stuffing your socks into separate drawers in your dresser solely based on the color of the sock... kinda dumb.

The reason for putting part of the code in a separate directory is for code reuse. I'm writing in C++ with OOD, and designing classes that can be reused by another project, just by copy & paste of the directory, even without altering the makefile. The bin directory stems from the root directory of the project, and is common to the whole project.

---

### Post by dwhitney67 on 2007-11-22
I think one can conjure up a dozen and half reasons for organizing their software the way the want, but I was referring to the organization of software for one CSC.

A former employee with my employer set up a directory structure similar to this, which IMO is crap (note, I have changed the names to protect the identity of the company):

```

SomeLib
       - include
              - boolean
                     - PredicateExpression.h
                     - PredicateList.h
              - callback
                     - CallbackFour.h
                     - CallbackOne.h
                     - CallbackThree.h
                     - etc
              - control
                     - DecisonTable.h
                     - ProcessWatcher.h
                     - Select.h
                     - etc
              - etc

       - source
              - boolean
                     - PredicateExpression.cpp
                     - PredicateList.cpp
              - control
                     - DecisionTable.cpp
                     - ProcessWatcher.cpp
                     - Select.cpp
                     - etc
              - etc

```

It would have been easier for system maintenance purposes (you know about that, don't you?) if all of the sources were in the same directory.  Ditto for the headers.  By scattering them around, one has to search (or rely on a tool) to find where a file resides.

When I am examining source code that includes one of the aforementioned header files, all I see is something like "#include "PredicateList.h".  If I want to take a peek at PredicateList.h, then I have to determine in which subdirectory of SomeLib/include it lives in; it would have been easier if my search ended at the include directory.

Here is a snip from the Makefile.  All of the sources file that are listed are used to make _one_ library.

```
LIB_SOURCES = boolean/PredicateExpression.cpp \
              boolean/PredicateList.cpp \
              control/DayCare.cpp \
              control/DecisionTable.cpp \
              control/OneShot.cpp \
              control/ProcessWatcher.cpp \
              control/Select.cpp \
              control/Signal.cpp \
              control/State.cpp \
              control/StateEngine.cpp \
              control/StateEngineImpl.cpp \
              convert/Base64.cpp \
              convert/Converter.cpp \
              error/ClassError.cpp \
              error/DataError.cpp \
              error/Error.cpp \
              error/FileError.cpp \
              error/ParseError.cpp \
              error/ProcessError.cpp \
              error/UpdateError.cpp \
              error/XMLError.cpp \
              file/DirectoryEntry.cpp \
              file/DirectoryInfo.cpp \
              file/File.cpp \
              file/FileInfo.cpp \
              file/FileSystemWatcher.cpp \
              file/FileSystemWatcherImpl.cpp \
              file/GlobalDirWatcher.cpp \
              file/GlobalDirectoryList.cpp \
              file/MegaFile.cpp \
              file/MetaDirectoryInfo.cpp \
              lib/LibraryLoader.cpp \
              log/Log.cpp \
              log/LogConfig.cpp \
              log/LogCoordinator.cpp \
              log/LogInternal.cpp \
              map/SubstringLookup.cpp \
              op/MathOp.cpp \
              op/PathOp.cpp \
              op/StringOp.cpp \
              parse/Closure.cpp \
              parse/DottedProduction.cpp \
              parse/ParsedValue.cpp \
              parse/ParseNode.cpp \
              parse/Parser.cpp \
              parse/ParseState.cpp \
              parse/Production.cpp \
              parse/ProductionGroup.cpp \
              parse/Token.cpp \
              parse/TokenValue.cpp \
              parse/Tokenizer.cpp \
              parse/Transition.cpp \
              statistic/AsimtoticAverage.cpp \
              statistic/RateLimiter.cpp \
              status/StatusAlarmInfo.cpp \
              status/StatusDepot.cpp \
              etc

```

Anyhow, I think it would have been a lot better to do away with the unnecessary level of directories that add no benefit to the project.  You may have a differing opinion, and that's fine.


P.S.  I have been developing software on *nix systems all my career (18+ years), never once relying on an IDE (idiot development environment).

---

