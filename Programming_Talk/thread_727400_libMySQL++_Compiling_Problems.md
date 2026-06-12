---
title: "libMySQL++ Compiling Problems"
date: 2008-03-17
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-03-17
Hi everyone, 

This is a similar problem to my[ recent battle with libxml++]("http://ubuntuforums.org/showthread.php?p=4530349"), but the solutions figured out in that thread don't apply to this... because I was told that mysql++ doesn't support pkg-config.

I jumped on the mailing list for mysql++ and got a response a few days ago to put together a meshed up Makefile based on my system settings.  So I took the gcc-based Makefile and the "base" Makefile, and put them together as instructed.

But it compiles with errors of needing definitions.

In "main.cpp":```

#include <mysql++/mysql++.h>
```

In "Makefile" (different blocks of code are noted as to where they came from) ```

#--------------------MySQL++ Makefile.gcc-----------
CXX=g++
INCLUDES=-I/usr/include/mysql -I../lib
CXXFLAGS=$(INCLUDES) -O0 -c

LD=$(CXX)
LDFLAGS=-L../lib
LDEXEFLAG=-o
LIBS=-lmysqlclient -lmysqlpp

EXTRA_CLEAN=

OBJ=o
EXE=
DEL=rm -f


.SUFFIXES: .cpp .o
.cpp.o:
	$(CXX) $(CXXFLAGS) $<


gcc: all
#--------------------MySQL++ Makefile.base-----------
define mk-objlist
	$(foreach O,$1,\
		$(if $(findstring $(BIN_DIR)/,$(O)),$(O),$(BIN_DIR)/$(O)))
endef

ifndef BIN_DIR
	BIN_DIR=.
endif

BINARIES=resetdb$(EXE) simple1$(EXE) simple2$(EXE) simple3$(EXE) \
		usequery$(EXE) fieldinf1$(EXE) dbinfo$(EXE) cgi_image$(EXE) \
		load_file$(EXE) updel$(EXE) multiquery$(EXE) custom1$(EXE) \
		custom2$(EXE) custom3$(EXE) custom4$(EXE) custom5$(EXE) \
		custom6$(EXE) 

RESETDB_OBJS=resetdb.$(OBJ) util.$(OBJ)
SIMPLE1_OBJS=simple1.$(OBJ) util.$(OBJ)
SIMPLE2_OBJS=simple2.$(OBJ) util.$(OBJ)
SIMPLE3_OBJS=simple3.$(OBJ) util.$(OBJ)
USEQUERY_OBJS=usequery.$(OBJ) util.$(OBJ)
CUSTOM1_OBJS=custom1.$(OBJ) util.$(OBJ)
CUSTOM2_OBJS=custom2.$(OBJ) util.$(OBJ)
CUSTOM3_OBJS=custom3.$(OBJ) util.$(OBJ)
CUSTOM4_OBJS=custom4.$(OBJ) util.$(OBJ)
CUSTOM5_OBJS=custom5.$(OBJ) util.$(OBJ)
CUSTOM6_OBJS=custom6.$(OBJ) util.$(OBJ)
FIELDINF1_OBJS=fieldinf1.$(OBJ) util.$(OBJ)
DBINFO_OBJS=dbinfo.$(OBJ) util.$(OBJ)
CGI_IMAGE_OBJS=cgi_image.$(OBJ)
LOAD_FILE_OBJS=load_file.$(OBJ)
UPDEL_OBJS=updel.$(OBJ)
MULTIQUERY_OBJS=multiquery.$(OBJ) util.$(OBJ)


all debug: $(BINARIES)

.PHONY: release
release:
	$(MAKE) BIN_DIR=release

clean:
	$(RM) $(LOCAL_CLEAN)


resetdb$(EXE): $(RESETDB_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

simple1$(EXE): $(SIMPLE1_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

simple2$(EXE): $(SIMPLE2_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

simple3$(EXE): $(SIMPLE3_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

usequery$(EXE): $(USEQUERY_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom1$(EXE): $(CUSTOM1_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom2$(EXE): $(CUSTOM2_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom3$(EXE): $(CUSTOM3_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom4$(EXE): $(CUSTOM4_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom5$(EXE): $(CUSTOM5_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

custom6$(EXE): $(CUSTOM6_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

fieldinf1$(EXE): $(FIELDINF1_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

dbinfo$(EXE): $(DBINFO_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

cgi_image$(EXE): $(CGI_IMAGE_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

load_file$(EXE): $(LOAD_FILE_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

updel$(EXE): $(UPDEL_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)

multiquery$(EXE): $(MULTIQUERY_OBJS)
	$(LD) $(LDFLAGS) $(LDSTARTUP) $(call mk-objlist,$^) $(LDEXEFLAG)$@ $(LIBS)


resetdb.$(OBJ): resetdb.cpp util.h
simple1.$(OBJ): simple1.cpp util.h
simple2.$(OBJ): simple2.cpp util.h
simple3.$(OBJ): simple3.cpp util.h
usequery.$(OBJ): usequery.cpp util.h
custom1.$(OBJ): custom1.cpp util.h
custom2.$(OBJ): custom2.cpp util.h
custom3.$(OBJ): custom3.cpp util.h
custom4.$(OBJ): custom4.cpp util.h
custom5.$(OBJ): custom5.cpp util.h
custom6.$(OBJ): custom6.cpp util.h
fieldinf1.$(OBJ): fieldinf1.cpp util.h
dbinfo.$(OBJ): dbinfo.cpp util.h
cgi_image.$(OBJ): cgi_image.cpp
load_file.$(OBJ): load_file.cpp
updel.$(OBJ): updel.cpp
util.$(OBJ): util.cpp util.h
multiquery.$(OBJ): multiquery.cpp util.h
#------------Custom Makefile-----------------
userGrab.ose:  main.cpp
	g++ main.cpp -o userGrab.ose
```

All I did was copy and paste in what it told me to.  I even tried reversing the order of the two.  But no luck.

Any ideas?

Thanks!

---

### Post by stevescripts on 2008-03-17
Posting the compilation errors sounds like a good thing at this point.

Steve

---

### Post by 71fnRVVm on 2008-03-17
Oh, sorry.  I meant to include it, but forgot.

The error from running "make":```

make: *** No rule to make target `resetdb.cpp', needed by `resetdb.o'.  Stop.

```

Thanks

---

### Post by stevescripts on 2008-03-17
A couple of questions ...

Did you run ./configure? If it finds everything it needs it will generate a makefile that should *just work*

(If you did, search config.log for errors - may be enlightening)

Do you have the mysqlclient libs installed (and the dev libs too)?

Is your stuff installed in one of the searched for locations?

That said, I d/loaded and built the stuff here tonight (open suse10.3),
kinda out of curiosity.  (had to grab mysql, the client lib and dev lib
to get it to build)

After all that, another question.  Are you strongly tied in to using
mysql in your projects?  

Personally, I am a big fan (and small-time user) of SQLite.  If you haven't checked it out - [http://www.sqlite.org/](http://www.sqlite.org/)

Hope this has been somewhat helpful.

Steve

---

### Post by 71fnRVVm on 2008-03-17
Hey Steve,

I didn't run ./configure, but when I did just now it said it couldn't find the command.

I have the libmysql++ (and dev), and libmysqlclient (-dev and off) installed... have from the get-go.

Installation?  I just installed it through a package installer on my Ubuntu machine... I didn't check, but it should all be there, since it self installed... right?

Yeah, I'm pretty into MySQL because this is going to sit on a server that the dB is MySQL... so unless there's an easier way to make MySQL queries from C++...?

Thanks

---

### Post by stevescripts on 2008-03-17
You need to run ./configure from the mysql++-3.0.0 directory.

Do you have a confiig.log in that directory?

Steve

---

### Post by stevescripts on 2008-03-17
Just a quick afterthought (getting late here, ready to give it up for the night).

The only time I have ever been forced to work on a mysql web project - the only interface available to us was PHP .... (enough said)

It has been years ago.  I *assume* mysql++ is the defacto standard for coding C++ queries for mysql.

Steve

---

### Post by 71fnRVVm on 2008-03-18
Ok, I don't think this ./configure answer is going to work, for some reason.

I tried it in all possible dirs:
/usr/include/mysql++
/usr/include/mysql
...and then even in some of the /usr/share/docs/ dirs that were related to MySQL, even though that was pretty obvious it wasn't going to work.

What about the Makefile data I posted earlier?  That's the answer I got from the mailinglist guys, but they won't respond anymore... I'm thinking that is probably where the solution lies?

Thanks

---

### Post by the_unforgiven on 2008-03-18
Why not just install it off [Ubuntu repositories]("http://packages.ubuntu.com/gutsy/libmysql++-dev")?
Is there a particular reason why you're trying to compile it from source?

The [filelist]("http://packages.ubuntu.com/gutsy/i386/libmysql++-dev/filelist") shows the actual files installed - which seems to satisfy your needs.

Please note that this package is part of Universe - you'd need to enable that in your repositories (/etc/apt/sources.list).

HTH ;)

---

### Post by 71fnRVVm on 2008-03-18
First of all, I did.

Second, I need to do it like this because it's going on a server that is NOT Ubuntu, and should be able to dynamically adapt to the environment when recompiled.

I thought that was obvious.

---

