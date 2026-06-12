---
title: "[C] makefile and glade problems"
date: 2009-03-31
forum: Programming Talk
---

### Post by sujoy on 2009-03-31
I have been working on a gtk project, actually using it to learn the development process ;) anyhow,

I ran into a couple of problems where I need some help.

1. I need to put the path of the glade file in the source code. However, where do I put the glade file? If I place it in src/, I can run the program from the src/ directory only. If I put in a separate glade directory, and hardcode the path in the source file, even then the same problem exists.

2. In the Makefile, do I add the glade file as a dependency?

EDIT: ok if I use full path for the glade file, then it works fine, however, how do I distribute the program? I will need to create the directories on the users system if it doesnt exists already :confused:

---

### Post by dwhitney67 on 2009-03-31
> **sujoy said:**
> ... I will need to create the directories on the users system if it doesnt exists already :confused:

And what is wrong with that?

Alternatively, consider using a directory that already exists (eg. /usr/local/bin).

---

### Post by kknd on 2009-03-31
Resource files usually goes to /usr/share. How to reference it is a problem, specially for portable applications. I usally write a .sh launcher that calculates the working directory.

Something like this (taken from tuxguitar launcher):

> 
DIR_NAME=`dirname "$0"`
DIR_NAME=`cd "$DIR_NAME"; pwd`
cd "${DIR_NAME}"


---

### Post by sujoy on 2009-03-31
Yes, /usr/local/bin would do, but say it is not there somehow. Then where do I place the code to create the directory and copy the glade file there? 
I am adding the structure and Makefiles just to make things clear, as to how, the build goes on as of now.

files inside trunk
```
[sujoy::intel][~/work/project_contacts/trunk]% ls
COPYING  Makefile  glade  include  src
[sujoy::intel][~/work/project_contacts/trunk]% 
```

files inside src
```
sujoy::intel][~/work/project_contacts/trunk]% ls src
Makefile  callback.c  main.c  preferences.c  status.c
[sujoy::intel][~/work/project_contacts/trunk]% 
```

files inside include
```
[sujoy::intel][~/work/project_contacts/trunk]% ls include 
callback.h  global.h  status.h
[sujoy::intel][~/work/project_contacts/trunk]% 
```

files inside glade
```
sujoy::intel][~/work/project_contacts/trunk]% ls glade 
gui.glade  gui.xml
[sujoy::intel][~/work/project_contacts/trunk]%
``` 

Makefile in trunk
```
[sujoy::intel][~/work/project_contacts/trunk]% cat Makefile 
CC = gcc
CFLAGS = -I./include `pkg-config --cflags gtk+-2.0`
LIBS = `pkg-config --libs gtk+-2.0`
LFLAGS = -export-dynamic

PROG = contacts
SRCS = src/main.c src/callback.c src/status.c
OBJS = $(SRCS:.c=.o)

all: $(PROG)

$(PROG):
	( cd src; $(MAKE) )
	( cp src/$(PROG) . )

.PHONY: clean

clean:
	(cd src; $(MAKE) clean )
	-rm -f $(PROG)
[sujoy::intel][~/work/project_contacts/trunk]% 
```

Makefile in src
```
[sujoy::intel][~/work/project_contacts/trunk]% cat src/Makefile 
CC = gcc
CFLAGS = -I../include `pkg-config --cflags gtk+-2.0`
LIBS = `pkg-config --libs gtk+-2.0`
LFLAGS = -export-dynamic

PROG = contacts
SRCS = main.c callback.c status.c
OBJS = $(SRCS:.c=.o)

$(PROG): $(OBJS)
	$(CC) -o $(PROG) $(OBJS) $(LIBS) $(LFLAGS)

%.o: %.c
	$(CC) -c $< -o $@ $(CFLAGS)

.PHONY: clean

clean:
	-rm -f $(OBJS) $(PROG) *~

main.o: ../include/callback.h ../include/status.h
callback.o: ../include/callback.h ../include/status.h ../include/global.h
preferences.o: ../include/global.h
status.o: ../include/status.h ../include/global.h
[sujoy::intel][~/work/project_contacts/trunk]% 
```

If things can be improved, and or optimised, please let me know. For now I am concentrating on these matters more than the code itself, as this is one area I have no knowledge about.

---

### Post by dwhitney67 on 2009-03-31
I think that kknd's suggestion is great; place your configuration or other data files in /usr/share/myapp (or in lieu of myapp, whatever directory name you choose).

As for your executable program, place it in /usr/bin or /usr/local/bin.

I noticed in your makefile that it is devoid of any installation statements, other than the copy for the executable program to the top-level directory where your primary Makefile resides.

Below is a listing of a Makefile I use to install my personal socket library.  Use something similar for yours.
```

# Copyright (C) 2009 David M. Whitney (aka "dwhitney67")
#
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, either version 3 of the License, or (at your option) any later
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with
# this program. If not, see <http://www.gnu.org/licenses/>.

VERSION := `cat ./version`
DIR1     = socket
DIR2     = socket++
HDR_DIR  = headers
HDRS    := `find $(HDR_DIR) -name '*.h' -exec basename {} \;`

LIB1     = libSocket.so
LIB2     = libSocket++.so

DEST     = /usr/local


all:
        @make -s -C $(DIR1) depend
        @make -s -C $(DIR1) $@
        @make -s -C $(DIR2) depend
        @make -s -C $(DIR2) $@


install: all
        @echo "Installing libraries in $(DEST)/lib..."
        @if [ ! -d $(DEST)/lib ]; then \
                mkdir -p $(DEST)/lib; \
        fi

        @if [ ! -d $(DEST)/include/Socket ]; then \
                mkdir -p $(DEST)/include/Socket; \
        fi

        @$(RM) $(DEST)/lib/$(LIB1)
        @$(RM) $(DEST)/lib/$(LIB2)

        @install -m 444 $(DIR1)/$(LIB1)* $(DEST)/lib
        @install -m 444 $(DIR2)/$(LIB2)* $(DEST)/lib

        @echo "Setting up symbolic links..."
        @ln -s $(DEST)/lib/$(LIB1).$(VERSION) $(DEST)/lib/$(LIB1)
        @ln -s $(DEST)/lib/$(LIB2).$(VERSION) $(DEST)/lib/$(LIB2)

        @echo "Installing header files in $(DEST)/include..."
        @for hdr in $(HDRS); \
        do \
                install -m 444 $(HDR_DIR)/$$hdr $(DEST)/include/Socket; \
        done

        @if [ `id -u` -eq 0 ]; then \
                /sbin/ldconfig; \
        fi
        @echo "All done!"


clean:
        @make -s -C $(DIR1) $@
        @make -s -C $(DIR2) $@


distclean:
        @make -s -C $(DIR1) $@
        @make -s -C $(DIR2) $@
        @echo Removing directory $(DEST)/include/Socket
        @$(RM) -r $(DEST)/include/Socket
        @echo Removing symbolic link $(DEST)/lib/$(LIB1)
        @$(RM) $(DEST)/lib/$(LIB1)
        @echo Removing $(DEST)/lib/$(LIB1).$(VERSION)
        @$(RM) $(DEST)/lib/$(LIB1).$(VERSION)
        @echo Removing symbolic link $(DEST)/lib/$(LIB2)
        @$(RM) $(DEST)/lib/$(LIB2)
        @echo Removing $(DEST)/lib/$(LIB2).$(VERSION)
        @$(RM) $(DEST)/lib/$(LIB2).$(VERSION)

```

Yes, it is a little complex, but the main thing to focus on is the default setting for DEST, and what is done if DEST does not exist in the "install" section of the Makefile.

P.S.  If you app requires a hard-coded path to a config file, you can always replace that path (using sed or other command) within the source file (or header file) using commands within the Makefile, and then afterwards compile the source file.

---

### Post by sujoy on 2009-03-31
Thanks kknd. That is good advice indeed.

@dwhitney67

Thanks for the Makefile, that cleared up quite a few doubts. I forgot about the install and distclean stuff totally :P

---

