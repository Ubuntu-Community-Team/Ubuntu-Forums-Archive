---
title: "Cross Platform Development"
date: 2008-06-16
forum: Programming Talk
---

### Post by Mythrandil on 2008-06-16
I'm starting development on my first cross platform (windows/linux) application. 

Firstly if anyone would like to drop a few general pointers when tackling this problem it would be great.

I will be coding in c++, my thoughts are to simply structure the classes to abstract away from the OS as much as possible and have "foundation" classes which interchange and handle the specific OS IO etc, and simply have a makefile for each platform which includes the relevant "foundation" classes for the platform.

Just want your expert thoughts on the matter before I go in head first and make a fundamental mistake.

Thanks

---

### Post by xlinuks on 2008-06-16
Without specifying what kind of app and (GUI) libraries you "can" use?
Anyway, what you're trying to do has been done dozens (if not hundreds and thousands) of times, just look at the approach Firefox took.
In other words (especially if it's a large app) it's gonna be very complicated.
Look at Java, Python as technologies that "kind of" make life easier (sometimes vice versa), they do exactly what you're trying to reinvent:

> classes to abstract away from the OS as much as possible and have "foundation" classes which interchange and handle the specific OS IO etc

---

### Post by LaRoza on 2008-06-16
> **Mythrandil said:**
> 
Just want your expert thoughts on the matter before I go in head first and make a fundamental mistake.


Stick to standard C++, and use libraries that exist for each OS. You can even use the same compiler (see my wiki for downloads)

---

### Post by pmasiar on 2008-06-16
> **Mythrandil said:**
> before I go in head first and make a fundamental mistake.

Too late you already committed one! :-)

Language is a tool. You know you want to use a hammer, but not sure what you want to build with it :-) CptPicard call those "speed kiddies" - little different from script kiddies.

Unless runtime effectiveness is paramount requirement (asked for, not your gut guess), you will be much better off using high-level productive cross-platform programming language with memory management, like Python, Ruby and friends.

---

### Post by Mythrandil on 2008-06-16
Ah yes forgot to mention, I am using wxWidgets for GUI as it is cross platform. Also using the g++ compiler and complying to ISO c++ as much as possible.

It's not a big app, just a small synchronisation app that will suit my needs.

Any advice about when it comes to compile time? Is there an elegant way to compile for multiple platforms?

Also what about differing linux distros, The version of wxWidgets I have installed utilises GTK, is this common to linux platforms?

Thanks again.

---

### Post by Mythrandil on 2008-06-16
> **pmasiar said:**
> Too late you already committed one! :-)

Language is a tool. You know you want to use a hammer, but not sure what you want to build with it :-) CptPicard call those "speed kiddies" - little different from script kiddies.

Unless runtime effectiveness is paramount requirement (asked for, not your gut guess), you will be much better off using high-level productive cross-platform programming language with memory management, like Python, Ruby and friends.

I absolutely agree that you should choose your language based on the task, however as I'm sure you can appreciate other factors can affect this choice. 

My choice of c++ was firstly due to my desire to further develop my c++ skills as I believe they will be a useful tool in my proffessional career. Secondly I am quite competant in C# and PHP so the familiar syntax is desirable. Thirdly being frustrated with writing managed apps that must carry a 50mb+ run time environment I wanted to write in a language which compiles to machine code, which thus eliminates Ruby from my language choice as it is a slow interpreted language.

I have absolutely no experience in python so was naturally not considered.

---

### Post by id1337x on 2008-06-16
> Firstly if anyone would like to **drop** a few general **pointers** when tackling this problem it would be great.

```
#include <stdio.h>
#include <stdlib.h>

int main( void ) {
	
	// Create the pointer:
	int *ptr;
	ptr = malloc( sizeof(int) );
	*ptr = 12;
	
	// Drop the pointer
	drop(ptr);
	return 0;
}

int drop( int *ptr ) {

	free(ptr);
	return 0;

}
```

> Any advice about when it comes to compile time? Is there an elegant way to compile for multiple platforms?

Well you can use Perl or Python for cross-platform development and it would make life much easier. They both have bindings for Wx and I think that it is also the most commonly used widget toolkit (Tk is the standard one though). The problem is that Tk is too primitive. It will definitely take a lot of work to do it in C/C++ though.

---

### Post by DavidBell on 2008-06-16
If you are already using wxwidgets you don't need to mess around with creating your own xplatform classes because wx is not just guis - it has xplatform classes for files, threads, etc.

As for compiling, just develop on one platform so your code compiles warning free. When this works switch to the other platform, recompile and fix any new warnings that show up. From that point there's a 99% chance you are good to go. You can mix compilers, using wxwidgets I've gone from vc in windows to gcc in linux without any problems.

DB

---

### Post by Mythrandil on 2008-06-16
> **DavidBell said:**
> If you are already using wxwidgets you don't need to mess around with creating your own xplatform classes because wx is not just guis - it has xplatform classes for files, threads, etc.

As for compiling, just develop on one platform so your code compiles warning free. When this works switch to the other platform, recompile and fix any new warnings that show up. From that point there's a 99% chance you are good to go. You can mix compilers, using wxwidgets I've gone from vc in windows to gcc in linux without any problems.

DB
Excellent, so basicly use wxWidget classes for as much as possible not just GUI and compile in each respective platform, ideal.

What about from linux distro to distro? Is my program compiled on Ubuntu likely to run into problems on say Gentoo?

---

### Post by DavidBell on 2008-06-16
> **Mythrandil said:**
> What about from linux distro to distro? Is my program compiled on Ubuntu likely to run into problems on say Gentoo?

I've never tried that but you can compile wx apps with static linked libs in which case it should work anywhere (provided there are the standard libs it links to like gtk etc). 

If you compile with dynamic linking the user would need to install xw libs on their system.

DB

---

### Post by LaRoza on 2008-06-16
> **Mythrandil said:**
> Ah yes forgot to mention, I am using wxWidgets for GUI as it is cross platform. Also using the g++ compiler and complying to ISO c++ as much as possible.

That should be easy. wxWidgets is easy to install in Windows (and I believe the Dev-C++ IDE can easily compile with it, it used mingw)

If you use standard C++ and wxWidgets you should have no problems.

---

