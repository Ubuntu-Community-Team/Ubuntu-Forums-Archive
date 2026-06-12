---
title: "geany does not compile, bloodshed does. why?"
date: 2010-05-31
forum: Programming Talk
---

### Post by idrinkwhisky on 2010-05-31
Hi,

i am brushing up my c++ knowledge and I was playing around with including header files and source files in a project.

Anyways, in geany it does compile but it refuses to build. When i take the exact same code and compile it in bloodshed it executes with no problems. 

Does anybody know why Geany does not build my code? Is it something in the way Geany handles projects? Can you recommend maybe another IDE which would work better? I don t want to go back to windows to code.

Thanks

---

### Post by soltanis on 2010-05-31
One IDE is compiling with different options than the other. This isn't the fault of any one of them, but rather either a misconfiguration or misunderstanding on the programmer's (your) part.

I would think both IDEs tell you what they are doing when they are compiling, so if you could post the commands they use and the errors you are getting, that would point us to the problem.

---

### Post by idrinkwhisky on 2010-05-31
Hi thanks for your very fast response,

bloodshed compiles with no problems so no comments there.
I have quoted the comments from geany below:

[COLOR="Red"]g++ -Wall -o "main" "main.cpp" (in directory: /home/user/cpp/projects2)
/tmp/ccmwYPZ0.o: In function `main':
main.cpp:(.text+0x1c): undefined reference to `Square(double)'
collect2: ld returned 1 exit status
Compilation failed.
[/COLOR]

Many thanks.

In case it helps the code that i wrote was:

// Header.h file
double Square(double x);

//Header.cpp
#include </home/user/cpp/projects2/Header.h>
 double Square(double Value)
 {
 /* Function code */
 double SquareReturn;

  SquareReturn = Value * Value;

 return SquareReturn;
}

//main.cpp
#include </home/user/cpp/projects2/Header.h>
#include <iostream>

int main (void)
{
 double Number;
 double SquaredNumber;

Number = 5;

SquaredNumber = Square(Number);


 std::cout << SquaredNumber;
 return 0;
}

---

### Post by Can+~ on 2010-05-31
```
#include </home/user/cpp/projects2/Header.h>
```

This is wrong, you should be using local references (for portability), and also, the <> only works when the files are on your path, I'm guessing this is the reason why it works in Mingw, it probably adds everything to the PATH.

Here's the "corrected" code:

header.cpp
[PHP]#include "header.h" // Local reference

double Square(double Value)
{
	/* Function code */
	double SquareReturn;

	SquareReturn = Value * Value;

	return SquareReturn;
}[/PHP]

header.h
[PHP]#ifndef HEADER_H_ // double include protection

double Square(double x);

#define HEADER_H_
#endif //HEADER_H_[/PHP]


main.cpp
[PHP]#include "header.h" // Again, local header
#include <iostream>

int main (void)
{
	double Number;
	double SquaredNumber;

	Number = 5;

	SquaredNumber = Square(Number);


	std::cout << SquaredNumber;
	return 0;
}[/PHP]

Compiled with (Not the pretty way):
```
g++ main.cpp header.cpp -o mystuff
```

Properly compiled and linked (the "right way" for makefiles):
```
g++ -c main.cpp header.cpp
g++ header.o main.o -o mystuff
```

Any GCC expert, feel free to bash me about anything, long time since I compile anything, so maybe I'm wrong somewhere.

---

### Post by idrinkwhisky on 2010-05-31
Ok thanks for your suggestions. I made the adjustments and now it runs from command line when i use g++ directly in the comand line.

however still no luck with Geany. Same error. I think it has to do with the header.cpp file. Whenever I dump the code from the header.cpp file directly into the headerfile (header.h) Geany will also compile. 
So it feels like it s a problem in linking the cpp files together in geany. 

I found this link in which the same problem is described:

[http://stackoverflow.com/questions/1483491/c-including-header-file-fails-compilation-but-including-source-cpp-file-compil](http://stackoverflow.com/questions/1483491/c-including-header-file-fails-compilation-but-including-source-cpp-file-compil)

I think I ll stop worrying bout geany and just use g++ and the terminal instead. thanks again (unless somebody knows how to link cpp files in geany)

---

### Post by Can+~ on 2010-05-31
The thing is, geany just compiles one-by-one, just take a look at "Build > Set Includes and Arguments". Geany has no way to tell that you'll compile/link more than one file at a time.

You could write a makefile, and just tell geany to run "make" on the folder; edit the geany command to do something else (example, compile everything in the folder like [FONT="Courier New"]g++ -c *.cpp, g++ -o *.o executable[/FONT]); or use another program entirely.

For C and C++ I usually use Eclipse with the cdt plugin, although, I think it would be overwhelming for a starter like you.

So yeah, stick with the terminal, that way you'll learn compiling by hand, it will be useful later.

---

### Post by trent.josephsen on 2010-05-31
> **idrinkwhisky said:**
> I think I ll stop worrying bout geany and just use g++ and the terminal instead.

Sound idea.  When that becomes tedious, learn to write Makefiles.

---

### Post by idrinkwhisky on 2010-05-31
thanks everybody

---

