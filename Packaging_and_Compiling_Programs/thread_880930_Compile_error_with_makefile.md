---
title: "Compile error with makefile"
date: 2008-08-05
forum: Packaging and Compiling Programs
---

### Post by Mandels on 2008-08-05
Hi!

I have a problem whit my program when i try to compile it.

This is my makeFile

```

# MakeFile
#================

#Compiler
CC = g++

#object Files
OBJS = main.o LogMethod.o

#Flags
DEBUG  = -g
CFLAGS = -Wall -c $(DEBUG)
LFLAGS = -Wall $(DEBUG)

p1 : $(OBJS)
	$(CC) $(LFLAGS) $(OBJS) -o p1
	
main.o: main.cpp LogMethod.h
	$(CC) $(CFLAGS) main.cpp
	
LogMethod.o: LogMethod.cpp LogMethod.h
	$(CC) $(CFLAGS) -Lusr/log4cpp/lib -llog4cpp -pthread LogMethod.cpp
	
clean: 
	\rm *.o *~ p1

```

and this is the output:

```

g++ -Wall -c -g main.cpp
g++ -Wall -c -g -Lusr/log4cpp/lib -llog4cpp -pthread LogMethod.cpp
g++: -llog4cpp: linker input file unused because linking not done
g++ -Wall -g main.o LogMethod.o -o p1
LogMethod.o: In function `LogMethod::logFile(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:27: undefined reference to `log4cpp::Category::getInstance(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:37: undefined reference to `log4cpp::Category::info(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
LogMethod.o: In function `LogMethod':
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:13: undefined reference to `log4cpp::FileAppender::FileAppender(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, bool, unsigned int)'
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:16: undefined reference to `log4cpp::BasicLayout::BasicLayout()'
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:13: undefined reference to `log4cpp::FileAppender::FileAppender(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, bool, unsigned int)'
/home/cristian/Desktop/ProvaMake/Core/main/LogMethod.cpp:16: undefined reference to `log4cpp::BasicLayout::BasicLayout()'
collect2: ld returned 1 exit status
make: *** [p1] Error 1
cristian@cristian-note:~/Desktop/ProvaMake/Core/main$ 


```


The files are:
--> main.cpp (incude LogMethod.h)
--> LogMethod.cpp
--> LogMethod.h  (include log4cpp library)

All file are in the same directory.

The program compile successfully with this command

```

g++ -Lusr/log4cpp/lib -llog4cpp -pthread main.cpp LogMethod.cpp

```

Wher is my error??

P.S. Sorry for my english! :lolflag:

Thanks

     Cristian.

---

### Post by meatpan on 2008-08-05
I think you are very close to a solution.  The makefile looks good, with the exception of the LogMethod.o target.

By using ${CFLAGS} in this particular compile command, you are including the '-c' compiler option, which informs the compiler that linking should not be performed.  This is causing the warning:
```

g++: -llog4cpp: linker input file unused because linking not done

```

In the subsequent steps, since LogMethod.o is not linked, the compiler cannot resolve the relevant logging symbols (which explains the compiler errors).

Consider appending
```

-Lusr/log4cpp/lib -llog4cpp

```

to the LFLAGS variable definition. Switch the order of vars in the p1 target to:
```

$(CC) $(OBJS) $(LFLAGS) -o p1

```
This helps ensure the dependencies are linked after being flagged as dependencies.

Let me know if this helps.

---

### Post by Mandels on 2008-08-05
Thanks for all,

I try your suggestion,
the makefile now is:

```

# MakeFile
#================

#Compiler
CC = g++

#object Files
OBJS = main.o LogMethod.o

#Flags
DEBUG  = -g
CFLAGS = -Wall -c $(DEBUG)
LFLAGS = -Wall $(DEBUG)

#Source
#LOGSOURCE = ../src/Log_File

p1 : $(OBJS)
	$(CC) $(OBJS) $(LFLAGS)  -o p1
	
main.o: main.cpp LogMethod.h
	$(CC) $(CFLAGS) main.cpp
	
LogMethod.o: LogMethod.cpp LogMethod.h
	$(CC) $(LFLAGS) -Lusr/log4cpp/lib -llog4cpp -pthread LogMethod.cpp
	
clean: 
	\rm *.o *~ p1

			 

```


 and now the error is this:


```

cristian@cristian-note:~/Desktop/ProvaMake/Core/main$ make
g++ -Wall -c -g main.cpp
g++ -Wall -g -Lusr/log4cpp/lib -llog4cpp -pthread LogMethod.cpp
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [LogMethod.o] Error 1
cristian@cristian-note:~/Desktop/ProvaMake/Core/main$ 


```

The compiler is unable to find the main reference...:confused:

Sorry but i understand this part of your replay:

> 
In the subsequent steps, since LogMethod.o is not linked, the compiler cannot resolve the relevant logging symbols (which explains the compiler errors).

Consider appending
Code:

```
-Lusr/log4cpp/lib -llog4cpp
```




where I append this flags?

---

### Post by meatpan on 2008-08-05
From my suggestions, your #Flags section should look like:

```

#Flags
DEBUG  = -g
CFLAGS = -Wall -c $(DEBUG) -pthread
LFLAGS = -Wall $(DEBUG) -Lusr/log4cpp/lib -llog4cpp -pthread

```
NOTE: I added -pthread to CFLAGS, since the preprocessor also needs this flag

The LogMethod.o target:

```

LogMethod.o: LogMethod.cpp LogMethod.h
	$(CC) $(CFLAGS) LogMethod.cpp

```

In your case, be sure you 'make clean' between unsuccessful builds.

---

### Post by Mandels on 2008-08-06
:guitar: Perfect, now i try to apply the suggestion to the makefile of my real program!

thanks for all!

---

### Post by Mandels on 2008-08-06
I hate makeFile ](*,)

I try to create a makeFile for my real program, adding step by step files and libraries, but...

The problem is similar to the precedent one.

this is my makeFile

```

# MakeFile
#================

#Compiler
CC = g++

#Source
SRCSOURCE = core/src
MAINSOURCE = core/main

#object Files
OBJS = $(MAINSOURCE)/faceEmotion.o $(SRCSOURCE)/VideoGrabber.o

#Flags
DEBUG  = -g
CFLAGS = -Wall -c $(DEBUG) -pthread 
LFLAGS = -Wall $(DEBUG) 
LOG4CPPFLAGS = -Lusr/log4cpp/lib -llog4cpp -pthread
OPENCVCONF = `pkg-config --libs opencv`
OPENCVFLAGS = `pkg-config --cflags opencv`

FaceEmotion : $(OBJS)
	$(CC) $(OBJS) $(LFLAGS) $(OPENCVFLAGS) -lm -lpthread -L/usr/lib $(OPENCVCONF) -o FaceEmotion
	
faceEmotion.o: $(MAINSOURCE)/faceEmotion.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(MAINSOURCE)/faceEmotion.cpp

VideoGrabber.o: $(SRCSOURCE)/VideoGrabber.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(SRCSOURCE)/VideoGrabber.cpp
	
clean: 
	\rm *.o *~ p1


```

and this is the error:

```

ristian@cristian-note:~/Desktop/Prova/FaceEmotion$ make
g++    -c -o core/main/faceEmotion.o core/main/faceEmotion.cpp
[B]In file included from core/main/faceEmotion.cpp:2:
core/main/../src/VideoGrabber.h:2:16: error: cv.h: No such file or directory
core/main/../src/VideoGrabber.h:3:21: error: highgui.h: No such file or directory[/B]
core/main/faceEmotion.cpp:27:2: warning: no newline at end of file
In file included from core/main/faceEmotion.cpp:2:
core/main/../src/VideoGrabber.h:27: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:27: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:28: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:28: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:28: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:29: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:29: error: &#8216;IplImage&#8217; has not been declared
core/main/../src/VideoGrabber.h:33: error: ISO C++ forbids declaration of &#8216;IplImage&#8217; with no type
core/main/../src/VideoGrabber.h:33: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
core/main/../src/VideoGrabber.h:34: error: ISO C++ forbids declaration of &#8216;CvMemStorage&#8217; with no type
core/main/../src/VideoGrabber.h:34: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
core/main/../src/VideoGrabber.h:35: error: ISO C++ forbids declaration of &#8216;CvCapture&#8217; with no type
core/main/../src/VideoGrabber.h:35: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
core/main/../src/VideoGrabber.h:39: error: ISO C++ forbids declaration of &#8216;CvHaarClassifierCascade&#8217; with no type
core/main/../src/VideoGrabber.h:39: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make: *** [core/main/faceEmotion.o] Error 1
cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ 


```

The compiler is unable to find the OPENVC libraries.

To write this make i use another makefile, which compiles successfully the program.

```

ifndef srcdir
srcdir = ./core/src
endif
ifndef maindir
maindir = ./core/main
endif

#-Lusr/log4cpp/lib -llog4cpp -pthread

CXX = g++
RM = rm -f
OBJ = $(patsubst $(srcdir)/%.cpp,$(srcdir)/%.o,$(wildcard $(srcdir)/*.cpp))  

MAINOBJ = $(patsubst $(maindir)/%.cpp,$(maindir)/%.o,$(wildcard $(maindir)/*.cpp))  
EXE = $(patsubst $(maindir)/%.cpp, % ,$(wildcard $(maindir)/*.cpp))


#CDEBUG = -fpic -ggdb

CFLAGS=-march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer
CXXFLAGS=${CFLAGS} ${CDEBUG}

OPENCVCONF = `pkg-config --libs opencv`
OPENCVFLAGS = `pkg-config --cflags opencv`
#LOG4CPPFLAGS = -Lusr/log4cpp/lib -llog4cpp -pthread

all: main 

main : $(OBJ) $(MAINOBJ)
	for m in $(EXE); do	\
		$(CXX) $(CXXFLAGS) $(OPENCVFLAGS) -lm -lpthread -L/usr/lib $(OPENCVCONF) -o $$m $(OBJ) $(maindir)/$$m.o #;	\
	done
	

%.o : %.cpp
	$(CXX) $(CXXFLAGS) -D_ENABLE_TILT -D_ENABLE_FORCE -I/usr/include/opencv/ -c $*.cpp -o $*.o

clean: 
	$(RM) $(srcdir)/*.o *~
	$(RM) $(maindir)/*.o *~


```

P.S. the file are
--->faceEmotion.cpp (main, include ../src/VideoGrammer.h)
--->VideoGrabber.cpp (include VideoGrabber.h)
--->VideoGrabber.h (include openCV (cv.h,highgui.h) libreries)

In my program moreover the VideoGrabber.h include LogMethod.h, but this is the next step!!

---

### Post by Mandels on 2008-08-06
...

---

### Post by meatpan on 2008-08-06
Be patient, working with build and deployment scripts (such as makefiles) takes practice.  The compiler messages can be cryptic, but informative if you know what to look for.

From the compiler output:
```

...
g++    -c -o core/main/faceEmotion.o core/main/faceEmotion.cpp
...

```

Notice that this is different from the directive in your makefile:
```

$(CC) $(CFLAGS) $(MAINSOURCE)/faceEmotion.cpp

```

There should be a '-Wall' and '-pthread' in the command, so you now have a hint that an error exists in your target/dependency specifications.

Now, to debug the script, walk through each of the targets and associated dependencies:

First:
FaceEmotion -> core/main/faceEmotion.o , core/src/VideoGrabber.o

Second:
core/main/faceEmotion.o: ??

Notice that the target 'core/main/faceEmotion.o' does not exist?  There is a target for 'faceEmotion.o', but this is very different (to the makefile ) from 'core/main/faceEmotion.o'.  The reason you still see the program trying to compile is that the makefile is executing the default compile command for a suffix of .cpp .  Suffix rules and suffix defaults are neat, and you should consult the online docs for more information.  For now, just understand that a suffix rule was applied when you meant to specify an action for a file.

In your makefile, change the target:
faceEmotion.o:

to 

$(MAINSRC}/faceEmotion.o

and 
VideoGrabber.o

to 

$(SRCSOURCE)/VideoGrabber.o


I think this will fix your issues.

---

### Post by Mandels on 2008-08-06
I try previously your suggestion, and the error was changed

Now i modify the makefile:

```

# MakeFile
#================

#Compiler
CC = g++

#Source
SRCSOURCE = core/src
MAINSOURCE = core/main

#object Files
OBJS = $(MAINSOURCE)/faceEmotion.o $(SRCSOURCE)/VideoGrabber.o

#Flags
DEBUG  = -g
CFLAGS = -Wall -c $(DEBUG) -I/usr/include/opencv/
LFLAGS = -Wall $(DEBUG) 
LOG4CPPFLAGS = -Lusr/log4cpp/lib -llog4cpp -pthread
OPENCVCONF = `pkg-config --libs opencv`
OPENCVFLAGS = `pkg-config --cflags opencv`

FaceEmotion : $(OBJS)
	$(CC) $(OBJS) $(LFLAGS) $(OPENCVFLAGS) -I/usr/include/opencv/ -lm -lpthread -L/usr/lib/ $(OPENCVCONF) -o FaceEmotion
	
$(MAINSOURCE)/faceEmotion.o: $(MAINSOURCE)/faceEmotion.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(MAINSOURCE)/faceEmotion.cpp

$(SRCSOURCE)/VideoGrabber.o: $(SRCSOURCE)/VideoGrabber.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(SRCSOURCE)/VideoGrabber.cpp
	
clean: 
	\rm *.o *~ p1

```

and the error:

```

cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ make
g++ -Wall -c -g -I/usr/include/opencv/ core/main/faceEmotion.cpp
g++ -Wall -c -g -I/usr/include/opencv/ core/src/VideoGrabber.cpp
core/src/VideoGrabber.cpp: In member function ‘bool VideoGrabber::analyzeCurrentFrame(bool, double*)’:
core/src/VideoGrabber.cpp:135: warning: control reaches end of non-void function
g++ core/main/faceEmotion.o core/src/VideoGrabber.o -Wall -g  `pkg-config --cflags opencv` -I/usr/include/opencv/ -lm -lpthread -L/usr/lib/ `pkg-config --libs opencv` -o FaceEmotion
[B]g++: core/main/faceEmotion.o: No such file or directory
g++: core/src/VideoGrabber.o: No such file or directory[/B]
make: *** [FaceEmotion] Error 1
cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ 
cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ 
 


```

Now the compiler find library, but it's unable to finds the two file

---

### Post by Mandels on 2008-08-07
:popcorn:

Ok i find a solution! whit this makefile

```

# MakeFile
#================

#Compiler
CC = g++
RM = rm -f

#Source
SRCSOURCE = core/src
MAINSOURCE = core/main

#object Files
OBJS = $(MAINSOURCE)/faceEmotion.o $(SRCSOURCE)/VideoGrabber.o

#Flags
DEBUG  = -g
CFLAGS = -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -c $(DEBUG) -I/usr/include/opencv/
LFLAGS = -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer $(DEBUG) 
LOG4CPPFLAGS = -Lusr/log4cpp/lib -llog4cpp -pthread
OPENCVFLAGS = -lm -lpthread -L/usr/lib/ 
OP = -I/usr/include/opencv/ -D_ENABLE_TILT -D_ENABLE_FORCE
OPENCVCONF = `pkg-config --libs opencv`
OPENCVPKG = `pkg-config --cflags opencv`

FaceEmotion : $(OBJS)
	$(CC) $(OBJS) $(LFLAGS) $(OPENCVPKG) $(OPENCVFLAGS) $(OPENCVCONF) -o FaceEmotion
	
$(MAINSOURCE)/faceEmotion.o: $(MAINSOURCE)/faceEmotion.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(MAINSOURCE)/faceEmotion.cpp $(OP) -o $(MAINSOURCE)/faceEmotion.o

$(SRCSOURCE)/VideoGrabber.o: $(SRCSOURCE)/VideoGrabber.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(SRCSOURCE)/VideoGrabber.cpp $(OP) -o $(SRCSOURCE)/VideoGrabber.o
	
clean: 
	$(RM) $(SRCSOURCE)/*.o *~
	$(RM) $(MAINSOURCE)/*.o *~

```

now next step!:)

thanks for all

---

### Post by Mandels on 2008-08-07
I have a new problem when I add the log4cpp library to compile LogMethod, in fact when i run the program the application fault with bad Flag error

Now the files are:
-> faceEmotion.cpp (include Videograbber.h)
-> VideoGrabber.cpp (include VideoGrabber.h)
-> VideoGrabber.h (include openCv libraries and LogMethod.h)
-> LogMethod.cpp (include LogMethod.h)
-> LogMethod.h (include log4cpp libraries)


I have modify the makefile adding the LogMethod file...

```

# MakeFile
#================

#Compiler
CC = g++
RM = rm -f

#Source
SRCSOURCE = core/src
MAINSOURCE = core/main

#object Files
OBJS = $(MAINSOURCE)/faceEmotion.o $(SRCSOURCE)/VideoGrabber.o $(SRCSOURCE)/LogMethod.o

#Flags
DEBUG  = -g
CFLAGS = -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -c $(DEBUG) -I/usr/include/opencv/
LFLAGS = -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer $(DEBUG) 
LOG4CPPFLAGS = -L/usr/log4cpp/lib -llog4cpp
OPENCVFLAGS = -L/usr/lib/ -lm -lpthread  
OP = -I/usr/include/opencv/ -D_ENABLE_TILT -D_ENABLE_FORCE
OPENCVCONF = `pkg-config --libs opencv`
OPENCVPKG = `pkg-config --cflags opencv`

FaceEmotion : $(OBJS)
	$(CC) $(OBJS) $(LFLAGS) $(OPENCVPKG) $(OPENCVFLAGS) $(OPENCVCONF) $(LOG4CPPFLAGS) -o FaceEmotion
	
$(MAINSOURCE)/faceEmotion.o: $(MAINSOURCE)/faceEmotion.cpp $(SRCSOURCE)/VideoGrabber.h
	$(CC) $(CFLAGS) $(MAINSOURCE)/faceEmotion.cpp -o $(MAINSOURCE)/faceEmotion.o

$(SRCSOURCE)/VideoGrabber.o: $(SRCSOURCE)/VideoGrabber.cpp $(SRCSOURCE)/VideoGrabber.h $(SRCSOURCE)/LogMethod.h
	$(CC) $(CFLAGS) $(SRCSOURCE)/VideoGrabber.cpp -o $(SRCSOURCE)/VideoGrabber.o

$(SRCSOURCE)/LogMethod.o: $(SRCSOURCE)/LogMethod.cpp $(SRCSOURCE)/LogMethod.h
	$(CC) $(CFLAGS) $(SRCSOURCE)/LogMethod.cpp -o $(SRCSOURCE)/LogMethod.o
		
clean: 
	$(RM) $(SRCSOURCE)/*.o *~
	$(RM) $(MAINSOURCE)/*.o *~

```

and the error is this

```

cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ make
g++ -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -c -g -I/usr/include/opencv/ core/main/faceEmotion.cpp -o core/main/faceEmotion.o
g++ -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -c -g -I/usr/include/opencv/ core/src/VideoGrabber.cpp -o core/src/VideoGrabber.o
core/src/VideoGrabber.cpp: In member function &#8216;bool VideoGrabber::analyzeCurrentFrame(bool, double*)&#8217;:
core/src/VideoGrabber.cpp:127: warning: control reaches end of non-void function
g++ -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -c -g -I/usr/include/opencv/ core/src/LogMethod.cpp -o core/src/LogMethod.o
g++ core/main/faceEmotion.o core/src/VideoGrabber.o core/src/LogMethod.o -march=i686 -mmmx -msse -msse2 -msse3 -O3 -pipe -Wall -fomit-frame-pointer -g  `pkg-config --cflags opencv` -L/usr/lib/ -lm -lpthread   `pkg-config --libs opencv` -L/usr/log4cpp/lib -llog4cpp -o FaceEmotion
cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ ./FaceEmotion 
Avvio riconoscimento
cleaning
OpenCV ERROR: Bad flag (parameter or structure field) (Unrecognized or unsupported array type)
        in function cvGetMat, cxarray.cpp(2881)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
cristian@cristian-note:~/Desktop/Prova/FaceEmotion$ 


```

I think the problem is the sum of flags of the log4cpp and opencv libreries... but there aren't errors when I compiling   :confused::confused:

---

### Post by Mandels on 2008-08-12
nothing?

---

