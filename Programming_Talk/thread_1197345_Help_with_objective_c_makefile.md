---
title: "Help with objective c makefile"
date: 2009-06-26
forum: Programming Talk
---

### Post by pointlesspoint on 2009-06-26
Hey everyone , i've been reading the board for years now , but never actually thought of asking a question since the search feature was always giving me enough information ...unfortunately this didn't happened with my latest diggins :).

Anyway , here's the case:

I have installed OBJC , and it compiles my program fine when im using command line , but when im using one of my makefile templates it fails without reason :confused:.

Here's my makefile :

```

CCC=gcc
CCFLAGS=-lgnustep-base -lpthread -lobjc -lm -lc -lSDLmain -I/usr/local/include/GNUstep -I/usr/include/GNUstep `sdl-config --libs --cflags`
SOURCES=    $(wildcard SRC/*.m) 
OBJECTS=    $(SOURCES:.m=.o)
EXECUTABLE=    out

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
    $(CCC) -o $@ $(OBJECTS)

clean:
    rm -f $(OBJECTS) $(EXECUTABLE)

.m.o:
    $(CCC) $(CCFLAGS) -c -o $@ $<

```

OUTPUT:
```

make: *** No rule to make target `SRC/main.o', needed by `out'.  Stop.


```

But when im using the command line , it compiles fine :
```

gcc -lgnustep-base -lpthread -lobjc -lm -lc -lSDLmain -I/usr/local/include/GNUstep -I/usr/include/GNUstep `sdl-config --libs --cflags`   main.m -o out

```Any ideas???:confused::confused:

---

### Post by nvteighen on 2009-06-26
I fear **.c.o**/**.cpp.o** is just allowed for those extensions. Replace the **.m.o** rule by:

(Careful, I indent here with 4 spaces... Replace by tab or it won't work)
```

%.o : %.m
    $(CCC) $(CCFLAGS) -c -o $@ $^

```

**$^** selects the sources one by one instead of taking them all together like **$<**. That's why you need it here... Think of it as an abbreviated foreach loop... (which also exists in Make, btw).

---

### Post by pointlesspoint on 2009-06-26
Wow , you're a god ! thanks!

But now there seems to be an issue : it seems to be ignoring my include directives , and im getting these errors:

```

SRC/main.o: In function `main':
main.m:(.text+0x70): undefined reference to `objc_get_class'
main.m:(.text+0x80): undefined reference to `objc_msg_lookup'
main.m:(.text+0x9a): undefined reference to `objc_msg_lookup'
main.m:(.text+0xb9): undefined reference to `objc_msg_lookup'
main.m:(.text+0xe0): undefined reference to `objc_msg_lookup'
main.m:(.text+0x110): undefined reference to `objc_msg_lookup'
SRC/main.o:main.m:(.text+0x136): more undefined references to `objc_msg_lookup' follow
SRC/main.o: In function `main':
main.m:(.text+0x15f): undefined reference to `SDL_Init'
main.m:(.text+0x17a): undefined reference to `objc_msg_lookup'
SRC/main.o: In function `__objc_gnu_init':
main.m:(.text+0x19e): undefined reference to `__objc_exec_class'
SRC/main.o:(.data+0x308): undefined reference to `__objc_class_name_NSObject'
collect2: ld returned 1 exit status
make: *** [out] Error 1


```
:confused:

---

### Post by nvteighen on 2009-06-26
You miss a **$(CCFLAGS)** at the $(EXECUTABLE) rule... Moreover, the **only place** where the -l tags are needed is there...

And... are you sure the headers are at /usr/**local**/include/GNUstep? That's pretty weird, they usually are at /usr/include/GNUstep... How did you install GNUStep?

EDIT: Something I came across... In these forums and other GNU/Linux devoted forums you'll get very little Objective-C help; ObjC is a language which is a lot associated to Mac OS X development and it's just ignored in other circles for no real reason... just "image". Sure, the most updated OpenStep library is the Apple NeXTStep Framework, but still... people don't seem to realize the potential ObjC has as a compromise solution between oversimple C and overbloated C++.

---

### Post by pointlesspoint on 2009-06-28
You were right , thanks! i got it working!

> 
EDIT: Something I came across... In these forums and other GNU/Linux devoted forums you'll get very little Objective-C help; ObjC is a language which is a lot associated to Mac OS X development and it's just ignored in other circles for no real reason... just "image". Sure, the most updated OpenStep library is the Apple NeXTStep Framework, but still... people don't seem to realize the potential ObjC has as a compromise solution between oversimple C and overbloated C++.   	

Yeah,i figured it out , but i don't think that i need help in code design / class implementation :p...

---

