---
title: "problem in make"
date: 2013-07-18
forum: Packaging and Compiling Programs
---

### Post by pulsarmnj on 2013-07-18
I am trying to make a package where I am getting error message

 f77 -O3  -c -o asind.o asind.fmake: f77: Command not found
make: *** [asind.o] Error 127


 
my makefile is like:

BIN = /usr/local/share/PACKAGE
FFLAGS = -O3
LDFLAGS = -L/usr/local/lib
LINK.f=gfortran $(FFLAGS) $(LDFLAGS)
LPGPLOT = -lpgplot -lcpgplot -L/usr/X11R6/lib -lX11


$(LIB)(asind.o) \
$(LIB)(beamfrac.o) \
$(LIB)(beaming.o) \
 .
.
.

all: survey populate visualize realpsrs pkspsrs underlying popjoin


survey : library survey.o $(LIB)
	$(LINK.f) -o $(BIN)/survey survey.o  $(LIB)


underlying : library underlying.o $(LIB)
	$(LINK.f) -o $(BIN)/underlying underlying.o  $(LIB)

.
.

---

### Post by dargaud on 2013-07-18
What happens if you just type 'f77' ? Command not found means that f77 is not installed. You can get it with "sudo apt-get install fort77" but there are plenty of different versions, so it may not be the one you want.

---

### Post by pulsarmnj on 2013-07-18
I do not want f77. I want to compile my codes with gfortran. So I have gfortran in my makefile. But from where is is calling f77, I can not understand. I even tried by setting aliases f77 to gfortran, but that did not help.

---

### Post by oldos2er on 2013-07-18
Moved to Packaging & Compiling Programs.

---

