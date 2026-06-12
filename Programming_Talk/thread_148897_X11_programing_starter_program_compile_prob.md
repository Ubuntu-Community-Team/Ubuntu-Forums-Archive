---
title: "X11 programing starter program compile prob"
date: 2006-03-22
forum: Programming Talk
---

### Post by dave_567 on 2006-03-22
Playing around with some X11 Programming.  I hit this web page and am having trouble compiling the example code. The link is:

[http://xander.ncl.ac.uk/game/index1.php](http://xander.ncl.ac.uk/game/index1.php)


////////////////////////////////////////////////////////////
me@ubuntu:~/Docs/C/XWindow/Pg1$ ./Makefile
./Makefile: line 2: go: command not found
./Makefile: line 3: main.cc: command not found
./Makefile: line 4: SRC:%.cc=%.o: command not found
./Makefile: line 5: -lX11: command not found
./Makefile: line 9: .SUFFIXES:: command not found
./Makefile: line 10: fg: no job control
./Makefile: line 11: CPP: command not found
./Makefile: line 11: DEF: command not found
./Makefile: line 11: INC: command not found
./Makefile: line 11: -o: No such file or directory
./Makefile: line 13: TARGET: command not found
./Makefile: line 13: all:: command not found
./Makefile: line 15: TARGET: command not found
./Makefile: line 15: OBJ: command not found
./Makefile: line 16: CPP: command not found
./Makefile: line 16: OBJ: command not found
./Makefile: line 16: LIB: command not found
./Makefile: line 16: -o: command not found
./Makefile: line 18: clean:: command not found
./Makefile: line 19: TARGET: command not found
me@ubuntu:~/Docs/C/XWindow/Pg1$ cat Makefile
CPP=g++
TARGET= go
SRC= main.cc win.cc
OBJ= $(SRC:%.cc=%.o)
LIB=-L/usr/X11/lib -lX11
INC=-I/usr/include/X11
DEF=

.SUFFIXES: .cc
%.o: %.cc
        $(CPP) $(DEF) $(INC) -g -c $< -o $@

all: $(TARGET)

$(TARGET): $(OBJ)
        $(CPP) -o $@ $(OBJ) $(LIB)

clean:
        rm -f *.o $(TARGET) core
///////////////////////////////////////////////////////////////

Copied the code into a directory.  Used chmod a+x to Makefile to create and executable.  Ran it and got junk.

I'm missing something basic here.  any help?

---

### Post by seanmc42 on 2006-03-23
Yes - you are missing something basic.
A makefile is not a script.

You should type "make".
Make is an application which looks for makefile and interprets its contents.

---

### Post by dave_567 on 2006-03-23
Well that is better.  Now I'm missing 'Xlib.h' and 'Xutil.h' fles.  Is this a library that I have not yet installed with umbumto or something I'll have to down load?  I've used the locate command and neither are on the hard drive. 

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

me@ubuntu:~/Docs/C/XWindow/Pg1$ make
g++  -I/usr/include/X11 -g -c main.cc -o main.o
In file included from main.h:4,
                 from main.cc:2:
win.h:4:22: error: X11/Xlib.h: No such file or directory
win.h:5:23: error: X11/Xutil.h: No such file or directory
win.h:14: error: ‘XEvent’ has not been declared
win.h:19: error: ISO C++ forbids declaration of ‘Display’ with no type
win.h:19: error: expected ‘;’ before ‘*’ token
win.h:22: error: ‘Window’ does not name a type
make: *** [main.o] Error 1
me@ubuntu:~/Docs/C/XWindow/Pg1$

---

### Post by seanmc42 on 2006-03-23
I'm not sure what package those are in.

Bring up synaptic. go to development.
Look fpr something like "X11 header files" or "X11 development" - if you can't find it, re-post and I'll look later (working now ;)

---

### Post by dave_567 on 2006-03-25
I finally got it.


```
sudo apt-cache search xlibs dev
```

then I installed all the development files associated with glut.  the program now works.  I can get down to learning the rest of the code from the web link.  
l

---

