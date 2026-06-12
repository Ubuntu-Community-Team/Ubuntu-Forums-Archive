---
title: "QT creator openmp problem"
date: 2011-11-15
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-11-15
Hello I have a problem with the openmp in QT Creator

It is ignoring the #pragma omp parallel macro, and I think I know why however I don't know how to solve it.

What I think is that the problem here:
```
  
p, li { white-space: pre-wrap; }  [COLOR=#1a1a1a]gcc -c -pipe -g -Wall -W -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I../fractal -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../fractal -I. -o fractal.o ../fractal/fractal.c[/COLOR]
 [COLOR=#b20808]../fractal/fractal.c: In function &#8216;GenerateImage&#8217;:[/COLOR]
 [COLOR=#b20808]../fractal/fractal.c:43:0: warning: ignoring #pragma omp parallel[/COLOR]

```I have the -fopenmp 
```

QMAKE_CXXFLAGS += -fopenmp
QMAKE_LFLAGS +=  -fopenmp

```And it is wokring however, it is added to g++ not gcc
```
g++ -fopenmp -o fractal fractal.o main.o    -L/usr/lib -lglut -lGLU -lQtGui -lQtCore -lpthread 
 make: Leaving directory `/home/jkalmar/data/fractal-build-desktop'

```However g++ works only with object files, the actual compilation is up to gcc, and I need the gcc to include -fopenmp

Any ideas?

---

### Post by Mr.Pytagoras on 2011-11-15
Never mind :)

As I was writing the post before I realize some things.
I have googled I little and here it is:
Insert this into .pro

for build target release
```
QMAKE_CFLAGS_RELEASE += -fopenmp
```
for debug
```
QMAKE_CFLAGS_DEBUG += -fopenmp
```

---

