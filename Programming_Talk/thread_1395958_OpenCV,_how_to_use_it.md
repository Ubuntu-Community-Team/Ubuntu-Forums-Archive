---
title: "OpenCV, how to use it?"
date: 2010-02-01
forum: Programming Talk
---

### Post by savagetwinky on 2010-02-01
I'm sure this has been answered before but i can't find the asnwer, after installing opencv from teh repositories how do i include that into a project i'm working on.
 
#include <cv.h>
deosn't work it can't find the header
 
i've also tried just unpacking it and building it in the same folder and using those inludes, didn't work, 
Then i tried following the instructions straight from the opencv wiki and still couldn't get it to work.
 
Its probably something stupidly simple i'm missing that i'm not really sure what i'm looking for so if any one can point me into the right direction for a guild to install opencv on 9.10 and how to compile a program using opencv that would be greatly appreciated.
 
I've heard installing it from the repositories is the easiest way to do it, but no one seems to explain what to do after words, i'm not too great at using linux yet but i'm learning.

---

### Post by rCXer on 2010-02-01
I use cmake to configure my OpenCV projects. I have no idea how to configure them manually.  While using cmake is somewhat tedious at first, it makes using multiple libraries across multiple platforms much easier.  Basically cmake finds the paths of the libraries and generates the makefiles. You only have to use it **once** per project. If you edit your program, just build it again. Look [here]("http://opencv.willowgarage.com/wiki/Getting_started") for more information on OpenCV and cmake.

Get cmake using...
```

sudo apt-get install cmake cmake-gui

```

* Create a folder, e.g. "ProgramFolder", for your program and put your source code, e.g. "Program.cpp", in it.  Create a file called "CMakeLists.txt" there and type the following in it.  (Always change **Program** to the name of your program!)
> 
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

PROJECT(**Program**)
FIND_Package(OpenCV REQUIRED)
INCLUDE_DIRECTORIES( ${OPENCV_INCLUDE_DIR} )
ADD_EXECUTABLE(**Program** **Program**.cpp)
TARGET_LINK_LIBRARIES(**Program** ${OPENCV_LIBRARIES})


* Run cmake-gui.  It should be under Applications -> Programming -> CMake.
-Tell cmake where the source code is.  Click on "Browse Source" and browse to your "ProgramFolder"
-Then tell cmake where to put the executable. Click on "Browse Build" and browse to your "ProgramFolder"
- Press "Configure", select "Unix Makefiles" and "Use Defaults" before pressing OK.
- Press "Configure" again.
- Press "Generate"

* If all goes well your "ProgramFolder" should have several new files including a Makefile
Navigate to your "ProgramFolder" in the terminal and enter...
```

make
./Program

```
...to build and run it.

Remember that you only have to use cmake **once**.  If you edit your program, just run "make" to build it again.

...And that's it :popcorn:

---

### Post by savagetwinky on 2010-02-05
thank you very much, but we ended up deciding to try to get everything running in windows, we were having issues with... everything, and we'll have to get it up in running on damn small linux later so instead of doing two different projects we figured we'd get damn small linux running on our hardware and prototype all the software the easiest way possible, but this will hopefully come in handy later.

---

