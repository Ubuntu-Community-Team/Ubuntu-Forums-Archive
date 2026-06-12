---
title: "missing gccmakedep from installing gcc"
date: 2006-08-02
forum: Programming Talk
---

### Post by overvisa on 2006-08-02
Hi there!
I have just installed gcc 4.0.3 via "apt-get install build-essential", but when i compile a c++ file, it shows up an error "gccmakedep: command not found". I look into /usr/bin/ and the gccmakedep is not there, instead, it should be there along with g++-4.0, gcc++-4.0... after I installed gcc ???. I did try to re-install gcc few times but there is still missing of gccmakedep ! 
Any help would be so much appriciated. I am so desperate at the moment :(

---

### Post by Grey on 2006-08-02
try "sudo apt-get install build-essential".  It's a metapackage that will install most things you need to compile things.

---

### Post by overvisa on 2006-08-02
Hi Grey, thanks a lot for your concern but 
as I said, I have installed gcc by "apt-get install build-essential" :(
Anyone who has tried "sudo apt-get install build-essential" would be able to check whether gccmakedep is in /usr/bin (as a directory contains gccbug, g++, gcc...). The gccmakedep is missing in my computer 
Or is there any way to install gccmakedep from a its own package? 
Please help !!!!!

---

### Post by Grey on 2006-08-02
Sorry, my mistake.  Don't know how I missed that.  But I just checked my system...  I regularly develop in both C and C++... I don't have that file either.  I had just assumed that it was part of the gcc set that I had never had a need for before.  (I don't really use much aside from gcc or g++).  I had a search through the ubuntu repositories... it's not there either:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gccmakedep&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gccmakedep&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386)

So having tried all that, I tried google, and I got this man page:
[http://www.hmug.org/man/1/gccmakedep.php](http://www.hmug.org/man/1/gccmakedep.php)

Which (I believe) says that it's the same as gcc -M?  I am not really clear on what it does, so I can't be sure.  At any rate, what are you trying to compile?

---

### Post by overvisa on 2006-08-02
Thanks for quick reply, Grey
I actually try to compile a piece of c++ codes provided from my teacher. I am totally new to linux as well as c++, this is some basic codes at a glance. However, I am still using gcc to compile and "make" other applications without any hassle. I believe the problem comes from the "gccmakedep" of the "makefile".This is my makefile (the gccmakedep is highlighted as red):

# Template Makefile to be used in Swinburne Linux labs
#
# Change the variables SRCS and TARGET to match your project,
# then execute "make all", or simply ¨make¨.
#
# Execute "make clean" to remove objects and executables from previous builds

# Note: g++34 is used to call GCC version 3 at Swinburne instead of version 2. 
# Replace with g++ to compile outside Swinburne.
CC  = g++ 

# Compiler flags (Add your choice to CLAGS):

# Turn on all warnings
WARNINGS = -Wall
# Enforce use of portable, ANSI/ISO standards-compliant C/C++ code
STRICT = -pedantic-errors
# Turn on C/C++ learning mode
LEARN_MODE = $(WARNINGS) $(STRICT)
# Include debugging info into executable
DEBUG = -g
# Optimise (moderately) for speed
FAST = -O2
# Optimise for size
SMALL = -Os

# You may edit the default compiler flags to add/remove your choices
CFLAGS = $(LEARN_MODE) $(DEBUG)

# Explicit rule that uses the redefined CC to compile C++ programs
%.o: %.cc
	$(CC) -c $(CFLAGS) -o $@ $<

# Enter the list of source files in your project
SRCS = Student.cc studentDrv.cc

# The list of object files is automatically constructed from source files
OBJS = $(SRCS:.cc=.o) 

# You may enter here any extra libraries to link against (e.g. -llibraryname)
LIBS = 

# List your targets (for example the executable you want made)
TARGET = studentDrv

all: depend $(TARGET)

$(TARGET): $(OBJS) Makefile
	$(CC) $(CFLAGS) $(OBJS) -o $(TARGET) $(LIBS)

.PHONY : clean depend

# This command automatically works out header file dependencies
depend :
	[COLOR="Red"]gccmakedep[/COLOR] -- $(CFLAGS) -- $(SRCS)

clean:
	rm -f $(OBJS) $(TARGET)
        

# DO NOT DELETE THIS LINE -- make depend depends on it.


I tried to replace gccmakedep as gcc -M and a bunch of errors come up when the makefile is compiled :confused: 
btw, I googled out downloadable gccmakedep package in here : [http://xorg.freedesktop.org/releases/individual/util/gccmakedep-1.0.2.tar.bz2](http://xorg.freedesktop.org/releases/individual/util/gccmakedep-1.0.2.tar.bz2)
but I don't know how to install it ,just to see it can fix this problem.

---

### Post by Grey on 2006-08-02
You need to download all the files from the cvs repository (sorry, that's out of the scope of this post, there should be instructions on the site), and then you can install it by doing this:

```

./configure
make
sudo make install

```

---

### Post by overvisa on 2006-08-03
thanks a bunch Grey, the problem is solved :p

---

