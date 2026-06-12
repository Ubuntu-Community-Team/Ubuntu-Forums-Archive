---
title: "SDL/SDL_image.h: No such file or directory"
date: 2009-10-20
forum: Programming Talk
---

### Post by swappo1 on 2009-10-20
A while ago I wrote a program that I am now trying to run on a new computer and I am getting the following errors.
```
hopchewer@hopchewer:~/Programming/gaming/Pong_file$ g++ -o pong pong.cpp -lSDL_image
pong.cpp:5:27: error: SDL/SDL_image.h: No such file or directory
pong.cpp: In function ‘SDL_Surface* load_image(std::string)’:
pong.cpp:128: error: ‘IMG_Load’ was not declared in this scope

```
I installed the following: libsdl1.2-dev libsdl1.2debian prior to running the program.  How do I get this running and get SDL to work again?

---

### Post by jpkotta on 2009-10-20
You also need libsdl-image1.2-dev.  You can use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for packages containing a certain filename.

---

### Post by WitchCraft on 2009-10-20
Next time:

```

apt-get install apt-file
apt-file update
apt-file search SDL_image.h

```

Which outputs the package where SDL_image.h is in.

---

### Post by WitchCraft on 2009-10-20
> **jpkotta said:**
> You also need libsdl-image1.2-dev.  You can use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for packages containing a certain filename.

```

apt-cache search PROGRAMNAME
apt-file search filename.h

```

Also, you need to link to this library.

---

### Post by dwhitney67 on 2009-10-20
You may also get greater mileage if you do something like:
```

g++ -o pong pong.cpp `pkg-config --cflags --libs sdl` -lSDL_image

```

---

### Post by swappo1 on 2009-10-20
If I use:
```
g++ -o pong pong.cpp `pkg-config --cflags --libs sdl` -lSDL_image
```
or:
```
g++ -o pong pong.cpp -lSDL_image
```
The program compiles and runs.  When I use my Makefile I get a ton of errors.

Output with Makefile:
```
hopchewer@hopchewer:~/Programming/gaming/Pong_file$ make
g++ -O2 -Wall -Werror -ansi   -c -o pong.o pong.cpp
cc1plus: warnings being treated as errors
pong.cpp: In member function ‘void Paddle1::get_input()’:
pong.cpp:264: error: enumeration value ‘SDLK_UNKNOWN’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_FIRST’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_BACKSPACE’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_TAB’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_CLEAR’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_RETURN’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_PAUSE’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_ESCAPE’ not handled in switch
pong.cpp:264: error: enumeration value ‘SDLK_SPACE’ not handled in switch
...
pong.cpp:272: error: enumeration value ‘SDLK_BREAK’ not handled in switch
pong.cpp:272: error: enumeration value ‘SDLK_MENU’ not handled in switch
pong.cpp:272: error: enumeration value ‘SDLK_POWER’ not handled in switch
pong.cpp:272: error: enumeration value ‘SDLK_EURO’ not handled in switch
pong.cpp:272: error: enumeration value ‘SDLK_UNDO’ not handled in switch
pong.cpp:272: error: enumeration value ‘SDLK_LAST’ not handled in switch
make: *** [pong.o] Error 1

```
Makefile:
```
CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = Pong
NAME = Pong
SRCS = pong.cpp
OBJS = pong.o

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		#mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)


```
I am not sure why I am getting this problem with my Makefile.  Everything worked on my laptop.

---

### Post by dwhitney67 on 2009-10-20
Maybe because you are optimizing?  Maybe because of the -ansi option?  Maybe because of the -Werror?

You are comparing apples to oranges.

My bet is that it is the optimization flag in conjunction with -Wall and -Werror that are causing you grief.  Account for the other possible enum values in your switch statement, or at a minimum place a default case, and I bet the warnings/errors will go away.

---

### Post by swappo1 on 2009-10-20
> Account for the other possible enum values in your switch statement, or at a minimum place a default case, and I bet the warnings/errors will go away.
A default case didn't clear up the errors.  Removing -Wall removed the errors.  
```
-O2 - Wall -Werror -ansi
```
Am I not supposed to be adding all these?  I don't know much about Makefiles.  I've just always included these and have never had any problems.

---

### Post by dwhitney67 on 2009-10-20
What you should have done is add a default case to your switch-block.  The compiler flags are fine, but as you found out, the -Wall is causing the warning to show up, and the -Werror is causing the warning to be treated as an error.

```

void Paddle1::get_input()
{
   SDLKey value;

   ...

   switch (value)
   {
      case SDLK_UNKNOWN:
          ...
          break;

      case SDLK_FIRST:
          ...
          break;

      ...

      // ADD a default case and the warning goes away!!!
      **default:**
          ...
          break;
   }

   ...
}

```

Btw, the compiler options have nothing to do with Makefiles.  You could have just as easily used those options on the command line.

---

### Post by unknownPoster on 2009-10-21
For debugging purposes, I never use optimization flags. All levels of optimization include the optimization "-fomit-frame-pointer" which means that the frame-pointer is not stored in a register. Because of this, tools such as gdb or valgrind are unable to step through your code.

---

### Post by swappo1 on 2009-10-21
> What you should have done is add a default case to your switch-block.
I did add a default case before removing -Wall but it didn't clear the errors up.  I will just leave the optimization flags out.  For some reason, I only have this problem on my desktop. I don't get these errors on my laptop.

---

### Post by WitchCraft on 2009-10-21
You id*ot, you use Werror.

From the gcc onlinedoc ([http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html) ):
> 
-Werror
Make all warnings into errors. 
-Werror=
Make the specified warning into an error. The specifier for a warning is appended, for example -Werror=switch turns the warnings controlled by -Wswitch into errors. This switch takes a negative form, to be used to negate -Werror for specific warnings, for example -Wno-error=switch makes -Wswitch warnings not be errors, even when -Werror is in effect. You can use the -fdiagnostics-show-option option to have each controllable warning amended with the option which controls it, to determine what to use with this option.
Note that specifying -Werror=foo automatically implies -Wfoo. However, -Wno-error=foo does not imply anything. 


Of course it compiles if you take out -Wall when you have -Werror on. That's because no more warnings are generated which -Werror could convert into errors...

Compile it with -Wall, then erradicate all warnings, then it compiles with -Werror.

---

