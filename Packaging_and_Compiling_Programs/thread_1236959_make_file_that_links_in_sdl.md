---
title: "make file that links in sdl"
date: 2009-08-10
forum: Packaging and Compiling Programs
---

### Post by iochinome on 2009-08-10
hey guys, so for the longest time in development with this little project ive been doing, i have just been doing simple #includes with .cpp files to simplify everything. sadly, i didnt turn to makefiles or even header files. just now i am making the transition. there are a few files involved, so i tried to make a makefile to simplify everything. the file containing main() is called main()

what i want to do is to also link in the necessary SDL files- it uses the SDL library, and, in the past, i have just taken the output of the command 
sdl-config --cflags --libs
and appended it to the end of the 
g++ -o program main.cpp
command. how do i work this into my makefile? here is what i have so far:
```

OBJS = main.o image_process.o controls.o
CC = g++ 
DEBUG = -g
CFLAGS = -Wall -c $(DEBUG)
LFLAGS = -Wall $(DEBUG)
SDLFLAGS = sdl-config --cflags --libs [IS THIS HOW I WOULD DO IT?]


program: $(OBJS) 
	$(CC) -o $(LFLAGS) $(OBJS) fovea  
main.o: main.cpp main.h image_process.h controls.h
	$(CC) $(CFLAGS) fovea.cpp
image_process.o: image_process.cpp image_process.h
	$(CC) $(CFLAGS) image_process.cpp
controls.o: controls.cpp controls.h
	$(CC) $(CFLAGS) controls.cpp

```

thanks guys!

---

### Post by iochinome on 2009-08-10
ok, for some reason i cant get this to work. i have 3 incredibly simple files now, just to make sure i understand whats going on, and it turns out i cant:

heres main.cpp:

```
#include <stdio.h>
#include <stdlib.h>
#include "functions.h"

int main() {
	print();
	return 0;
}
```

functions.cpp:
```
#include <stdio.h>
#include <stdlib.h>

#include "functions.h"

int x = 5;

int print() {
	printf("hello world!");
	return 0;
}

```

functions.h:
```
#ifndef FUNC_H
#define FUNC_H

int x;

int print();

#endif
```

and the makefile:
```
main: main.o functions.o
	g++ -o main main.o functions.o 
main.o: main.cpp functions.h
	g++ -c main.cpp
functions.o: functions.cpp functions.h 
	g++ -c functions.cpp
```

this always trips up... i dont get it! it tells me i have a redefinition of 'int x' in functions.cpp. whats going on here? thanks!

---

### Post by TrueTom on 2009-08-11
```
#ifndef FUNC_H
#define FUNC_H[B]

extern[/B] int x;

int print();

#endif
```

---

### Post by iochinome on 2009-08-11
great, thanks! so now how do i add in the SDL-linking? thanks-

---

### Post by iochinome on 2009-08-11
oh, and by the way, how does one go about defining a structure that multiple files can use? would i, say, put it in functions.h like this:

```

struct person;

```

and then define it like this in functions.cpp
```

struct person {
     int age;
     bool gender;
};

```
?
for some reason that doesnt work for me. thanks!

---

