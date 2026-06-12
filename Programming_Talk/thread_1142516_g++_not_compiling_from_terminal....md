---
title: "g++ not compiling from terminal..."
date: 2009-04-29
forum: Programming Talk
---

### Post by David C. on 2009-04-29
I discovered this site [**[COLOR="Blue"]ubuntu-gamedev[/COLOR]**]("http://ubuntu-gamedev.wikispaces.com/") and stumbled upon some pretty neat HowTo tuts about 2D and 3D game dev in Ubuntu. Great!  

I attempted the first basic tutorial [**[COLOR="Blue"]How-To+Setup+SDL+for+games+development[/COLOR]**]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development")
and did what was instructed...HOWEVER...I got to experience an error that I've been getting lately when using the terminal. An error telling me the file and/or directory is not found, even after I physically open the gui and look. I enter "ls" and it shows the file and/or directory. Why is it when I go through the window/gui & create a file or file folder, the console doesn't recognize it? But yet entering "mkdir dir" there it is smiling at me with a devilish grin. 

I created the file sdl_test.cpp in a text editor, saved it as such in /home/jdc/source. As per the tutorial, entered:
```

g++ -o sdl_test sdl_test.cpp -lSDL
./sdl_test
```

The response:
```
g++: sdl_test.cpp-1sdl: No such file or directory
g++: no input files

```

Okay. Moved the file from source into jdc, tried again...same error. Hmmm...so, I tried "touch sdl_test.cpp" to create a file within the jdc directory. It did. I opened it in the text editor to check if the code was there, it was. Entered the command as above and received the same error as above. I doubled checked synaptic to ensure I had the g++ compiler marked, it is. I tried building and running it in Code::Blocks...nothing but errors. 

For those familiar w/C++, is the code in the tut correct? Am I doing something wrong to compile the code. What input files need I add? Any help is much appreciated. Thanks.

EDIT: I believe I fixed it...sorry. I mistook the small "L" for a 1 in "lSDL"

---

### Post by dwhitney67 on 2009-04-29
You need to verify that there is source code in the file in the present working directory where you are attempting to run g++.

Touching a file, where it does not exist, merely creates an empty file.  The fact that you were able to edit your source using the IDE does not imply that you were editing the same file that was touched... unless of course you provide more evidence.

Anyhow, launch a terminal.  This should put you in your home directory, /home/jdc. Then change directory to source, verify the source code exists, then build your app:
```

cd source
cat sdl_test.cpp
g++ -o sdl_test sdl_test.cpp -lSDL

```

---

### Post by David C. on 2009-04-29
I saw the empty file and deleted it. I don't know if the sdl_test.cpp next to it was the original I created, though I believe so. It was the first time I used the touch command. Still learning all the little nuiances of Linux. 

As for the file, I did manage to get it to work. Only after my first post did I notice my typo error, mistaking the lower case "L" for the number one. I corrected it, entered the last part ./sdl_test...worked. Thanks for the input dwhitney67. Amazing how the smallest (dumbest) errors can cause the biggest headaches.

---

### Post by dwhitney67 on 2009-04-29
I'm glad I could help.

It is great that you are attempting to build from the command line.  Many new developers like to jump into using an IDE, and do not get to fully appreciate/understand what it takes to build an application, especially one with perhaps multiple source files.

Eventually, or maybe even today, you may want to consider using a Makefile to build your projects.

A typical one for basic SDL development would look like:
```

APP      = appname

SRCS     = $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)

INCLUDES =
CXXFLAGS = -g3 -Wall -pedantic $(INCLUDES)

LDFLAGS  =
LIBS     = -lSDL

DEP_FILE = .depend

.PHONY: all clean distclean


all: depend $(APP)

$(APP): $(OBJS)
        $(CXX) $^ $(LDFLAGS) $(LIBS) -o $@

clean:
        $(RM) $(OBJS)

distclean: clean
        $(RM) $(DEP_FILE)
        $(RM) $(APP)

depend: $(DEP_FILE)
        @touch $(DEP_FILE)

$(DEP_FILE):
        @echo Building dependencies in: $@
        @$(CXX) -E -MM $(INCLUDES) $(SRCS) > $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```
With Makefiles, everywhere there is a statement that is indented, that is a tab-space, not regular white-space.

---

### Post by David C. on 2009-04-30
I've "heard" of makefile on various forums, but am not familiar with it or what it does per se. As mentioned, I'm new to Linux, moving from XP and am still getting accustomed to how it works. I'm still not sure where to place an app that I want to manually install from tar.gz. With windows it was download, unzip, click the .exe file and the wizard set up did the rest. But I digress--back to the above code that you shared...

Is this entered in a IDE or in a text editor? How would I use it?  I'm new to programming in general, so bear with me, and am working to understand how a game app is developed. There's so much info out there that I'm getting overwhelmed trying to figure out how everything ties in--the game engine, SDL, OpenGL, OpenAL, etc, etc  The tutorials on SDL programming, OpenGL programming, game engine (open source) all vary.

I went thru another tut from the site I mentioned, trying to display a bmp, but instead of using the example bitmap, I inserted my own, but my image wouldn't display in the screen when I ran the code, it displayed the original bitmap image. Still working on figuring that one out. I know it's something I'm not catching.

Thanks again for the assist and the code example.

---

### Post by dwhitney67 on 2009-04-30
One would edit the Makefile using their favourite editor.  Typically the Makefile resides next to the source code (i.e. in the same folder), but that is not a requisite.

Once the Makefile is in place, you invoke it from the command like as such:
```

make

```

---

### Post by Neheb on 2009-04-30
if you want to try learning to make makefiles I would suggest starting with [http://www.gnu.org/software/make/manual/make.html]("http://www.gnu.org/software/make/manual/make.html"). I recently switched from using windows to program c++ and the above page made it really easy to get the basic of makefiles down.

I have nowhere near what dwhitney67 posted in my makefiles, but they get my small projects built easy.

also I think [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) was a really good tutorial to get started with SDL.

---

### Post by stevescripts on 2009-04-30
> **dwhitney67 said:**
> 
...
It is great that you are attempting to build from the command line.  Many new developers like to jump into using an IDE, and do not get to fully appreciate/understand what it takes to build an application, especially one with perhaps multiple source files.
...


Amen.

---

### Post by David C. on 2009-04-30
Thanks for the resources Neheb.

---

### Post by ov3rcl0ck on 2009-05-01
be sure to cd into the directory with the source code in it, and execute
"g++ sdl_test.cpp -lSDL -o sdl_test"
I think the parameters come after the input file, if that doesn't work use Eclipse, NetBean, CodeBlocks or another IDE that supports SDL development.

---

### Post by Neheb on 2009-05-02
> **ov3rcl0ck said:**
> be sure to cd into the directory with the source code in it, and execute
"g++ sdl_test.cpp -lSDL -o sdl_test"
I think the parameters come after the input file

From what I have tried g++ seems to not care much where you put things (except sdl_test right after -o etc(in this case)). If anyone know what is the proper/best/most common way to structure the g++ calls I would love to know.

---

### Post by dwhitney67 on 2009-05-02
> **Neheb said:**
> From what I have tried g++ seems to not care much where you put things (except sdl_test right after -o etc(in this case)). If anyone know what is the proper/best/most common way to structure the g++ calls I would love to know.

Usually the following is acceptable practice:
```

g++ [CXXFLAGS] file1.cpp [file2.cpp ... fileN.cpp] [LDPATH] [LIBS] [-o progname]

```
When dealing with many source files, it is desirable to compile the source code to form object files that can then, at a later stage, be linked together to form the executable program.

In this case, the steps are:
```

g++ [CXXFLAGS] -c file1.cpp
g++ [CXXFLAGS] -c file2.cpp
...
g++ [CXXFLAGS] -c fileN.cpp

g++ file1.o file2.o ... fileN.o [LDFLAGS] [LIBS] [-o progname]

```

Typical CXXFLAGS are -Wall -pedantic -ansi, but can include others, such as -I statements for specifying header file directories, or -g for indicating that you want symbolic information included in the executable (this is handy when you plan to debug the app).

LDFLAGS are generally the -L<libpath>.

LIBS are the libraries (eg. -lSDL).  On occasion, it is desirable to statically link a library into the program; the -static flag can be used.

The ordering of libraries within LIBS is important, especially if one library is dependent upon another.

The -o option is optional; without it, an a.out is produced.

---

