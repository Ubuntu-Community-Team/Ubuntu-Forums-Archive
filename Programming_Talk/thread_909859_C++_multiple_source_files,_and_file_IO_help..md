---
title: "C++ multiple source files, and file IO help."
date: 2008-09-03
forum: Programming Talk
---

### Post by shadoweva00 on 2008-09-03
I'm trying to write an AI program starting with the file writing functions. This would be my first project that requires being broken into multiple files and I'm running into a lot of problems my book and internet documentation aren't helping me with.

First, when I move the functions to a file that doesn't have main in it, I can't call the other functions from within a function. Can someone explain this?

Second, no matter what, I can't seem to get file IO outside of main in a reasonable manner. Ideally, I would like to open the file, and then run some different functions that write to it, and then close it; but that seems to require passing the reference, and even just trying to pass the value will result in "undefined identifier" error.

---

### Post by NovaAesa on 2008-09-04
I would suggest breaking the problem down into classes (seeings that the language of choice, C++ is mainly object orrientd). You would then put each class into it's own .cpp and .h files.

---

### Post by mujambee on 2008-09-04
> **shadoweva00 said:**
> 
First, when I move the functions to a file that doesn't have main in it, I can't call the other functions from within a function. Can someone explain this?

You need to declare the functions in your second module:

Your second module:

[php]
void myfunc( void )
{
	// do something
}
[/php]

Then, in your main module, you declare your func:

[php]
void myfunc( void );

int main( int argc, char **argv)
{
	myfunc();
}
[/php]

This is best done by creating you own include files:

myfunc.cpp
[php]
void myfunc( void )
{
	// do something
}
[/php]

myfunc.h
[php]
void myfunc( void );
[/php]

main.cpp
[php]
#include "myfunc.h"

int main( int argc, char **argv)
{
	myfunc();
}
[/php]



> **shadoweva00 said:**
> 
Second, no matter what, I can't seem to get file IO outside of main in a reasonable manner. Ideally, I would like to open the file, and then run some different functions that write to it, and then close it; but that seems to require passing the reference, and even just trying to pass the value will result in "undefined identifier" error.

References should work:


[php]
#include <iostream>
#include <fstream>

void myfunc( std::ofstream &in )
{
	int myvar = 1;

	in << myvar;
}
[/php]
[php]
#include <iostream>
#include <fstream>

void myfunc( std::ifstream &in );

int main( int argc, char ** argv )
{
	std::ofstream if( "/home/me/myfile" );

	myfunc( if );
}
[/php]

---

