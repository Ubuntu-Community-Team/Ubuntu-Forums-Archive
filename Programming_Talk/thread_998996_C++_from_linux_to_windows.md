---
title: "C++ from linux to windows"
date: 2008-12-01
forum: Programming Talk
---

### Post by brexsis on 2008-12-01
hi! i need to do programming in c++, i use windows only for games and linux for everythig else, and i want it that way, so i want to do programming in linux (Kubuntu64 8.10). at the end i need to give the teacher a windows exe file with some other aditional files (so the programm can run under windows). 
my question is - can i do the programming in linux, and then take files to windows OS and compile it in windows? can that work? my homework is to make a "Tower of Hanoi" : [http://netgames.apollo.lv/flashgame/31921](http://netgames.apollo.lv/flashgame/31921)
and is that OK, that i am doing it on 64bit linux?

---

### Post by dribeas on 2008-12-01
> **brexsis said:**
> hi! i need to do programming in c++, i use windows only for games and linux for everythig else, and i want it that way, so i want to do programming in linux (Kubuntu64 8.10). at the end i need to give the teacher a windows exe file with some other aditional files (so the programm can run under windows). 
my question is - can i do the programming in linux, and then take files to windows OS and compile it in windows? can that work? my homework is to make a "Tower of Hanoi" : [http://netgames.apollo.lv/flashgame/31921](http://netgames.apollo.lv/flashgame/31921)
and is that OK, that i am doing it on 64bit linux?

If you only use standard C++ and multiplatform libraries/frameworks then it should compile properly in windows. If you do use some system calls (I don't think you will for that app, but here it is) you can use cygwin to provide a unix layer over the windows platform. Anyway, I would always go for a multiplatform lib before cygwin/mingw.

For a simple programming assignment where there are no system calls, you will be fine with standard C++ and you can use either mingw/cygwin/vs.c++ express edition for compiling.

---

### Post by WitchCraft on 2008-12-01
> **brexsis said:**
> hi! i need to do programming in c++, i use windows only for games and linux for everythig else, and i want it that way, so i want to do programming in linux (Kubuntu64 8.10). at the end i need to give the teacher a windows exe file with some other aditional files (so the programm can run under windows). 
my question is - can i do the programming in linux, and then take files to windows OS and compile it in windows? can that work? my homework is to make a "Tower of Hanoi" : [http://netgames.apollo.lv/flashgame/31921](http://netgames.apollo.lv/flashgame/31921)sy
and is that OK, that i am doing it on 64bit linux?

If you need the gcc/g++ compiler, use MinGW & Msys.
Everything else does not work properly (differences between GNU & MS-VC, and cygwin requires the cygwin.dll, so it will fail to execute if your teacher doesn't have cygwin.dll installed...).

[www.sourceforge.net](www.sourceforge.net)

Good luck, if you use MinGW, you shouldn't need it!

---

### Post by mmix on 2008-12-01
It is ok, c compiler is portable.

[http://downloads.sourceforge.net/codeblocks/codeblocks-8.02mingw-setup.exe](http://downloads.sourceforge.net/codeblocks/codeblocks-8.02mingw-setup.exe)

---

### Post by CptPicard on 2008-12-01
While the response is that you "can" do it, if I were you, I would not risk failing a homework assignment simply because your prof fails to grade your work because you insisted on introducing the complications of cross-compilation into the picture... it just is not a wise strategy.

---

### Post by bfhicks on 2008-12-01
I think it's kind of weird that your teacher wants an executable. I never had a professor so trusting...

---

### Post by jimi_hendrix on 2008-12-01
> **bfhicks said:**
> I think it's kind of weird that your teacher wants an executable. I never had a professor so trusting...

put a line in your executable that makes a blank file with the name linux rules

---

### Post by brexsis on 2008-12-01
> **jimi_hendrix said:**
> put a line in your executable that makes a blank file with the name linux rules
i have no that understanding teacher :D

i will need to give the printed version of code with some explanation with it (so the teacher knows that i know i am doing), and show the game how it works (i assume that i will need executable, because i havent seen another OS than windows on her computer) . and i have no laptop :(


later i will try to run windows c++ version with wine.

---

### Post by jimi_hendrix on 2008-12-01
just delete the line about the file in your source...

---

### Post by Pagh on 2008-12-01
Hi there.

Some time ago i posted a similar question. Here is a link to the thread that explains how to handle cross-compiling between Ubuntu and Windows. Take a particularly good look at the last two posts. 

Hope the thread will somewhat answer your questions.

All the best 
            Kasper Roland Pagh

---

### Post by jimi_hendrix on 2008-12-01
no link?

---

### Post by brexsis on 2008-12-01
i cant install c++ with wine :(
so, i am really confused now...
in what programm i need then to do programming? i can find mingw32-binutils, but msys i even cant find in adept package manager. these are compilers, if i didnt mess with something in my head.
but what program i need to install, to do programming?...
i dont want to make file, then compile it manualy and then test manualy (like at begining in this topic: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)), i want like in windows, program something, pres 2 keys and program runs (if it is correct) (i dont care if it is windows style or dos like style)... is it possible here?
can i use Code::Blocks?

imaybe needed to mention this, that originally i need to programm that game in DOS like environment, very simple game, no mouse...

---

### Post by CptPicard on 2008-12-01
You really are trying to complicate this way beyond your capacity for a relatively simple programming class.

If you want to learn to program on Linux, you need to program on and for Linux, by using Linux tools and methods. This means that you need to be at least somewhat proficient at running the compiler from the command line, because that is fundamentally how the stuff works here.

Now, cross-compilation is a somewhat advanced exercise to begin with, and if you really have an added requirement that you want the Windows-style programming environment to go with it... you don't want to go the length of trying to set it up and get it working within the context of your class.

Just do this exercise on Windows, then come back to Linux, forget about trying to force Linux to become Windows, and start learning...

---

### Post by dribeas on 2008-12-02
> **CptPicard said:**
> You really are trying to complicate this way beyond your capacity for a relatively simple programming class.

Now, cross-compilation is a somewhat advanced exercise to begin with.

Just do this exercise on Windows, then come back to Linux, forget about trying to force Linux to become Windows, and start learning...

+1

I don't think you should really try to cross compile. Just get a C++ compiler in a windows box. I bet that the code you write in linux will directly compile in a windows compiler, in any case, you can program it in windows and later try to see if it will compile under linux.

---

### Post by lisati on 2008-12-02
Maybe a "console mode" program might be a place to get the basics of the exercise sorted out, with the option of adding an OS-specific wrapper later on, passing options via the command line arguments.

---

### Post by brexsis on 2008-12-02
i installed wirtualbox and borland c++ runs OK, some time ago, i had another version on Ubuntu, but then c++ vas wery slow under virtualbox, so i didnt even tried it on new Kubuntu until yesterday.
tnx everyone for helping me, now i will do my programming under virtual Windows :)

---

### Post by Delever on 2008-12-02
[DevC++]("http://www.bloodshed.net/devcpp.html") is what many people use. You can also use VS Express C++, but your program will require small runtime for that. As long as you use only STD library, it's easy, but things get messy if you want to throw some other libraries into the picture. However, I imagine that in your case it will actually be more C than C++ anyway...

---

### Post by WitchCraft on 2008-12-05
OK, links:

go to:
[http://sourceforge.net/project/showfiles.php?group_id=2435](http://sourceforge.net/project/showfiles.php?group_id=2435)

You need: 
Automated MinGW Installer
 - direct link: [http://downloads.sourceforge.net/mingw/MinGW-5.1.4.exe?modtime=1209244789&big_mirror=1](http://downloads.sourceforge.net/mingw/MinGW-5.1.4.exe?modtime=1209244789&big_mirror=1)
MSYS Base System (current release)
 - direct link: [http://sourceforge.net/project/downloading.php?group_id=2435&use_mirror=garr&filename=MSYS-1.0.10.exe&48343111](http://sourceforge.net/project/downloading.php?group_id=2435&use_mirror=garr&filename=MSYS-1.0.10.exe&48343111)


Now first install MinGW with g++ (C compiler will be installed anyway.)
(install with the values the installer suggests, everything else might not work)

Then install the msys base system

you need to point msys to c:/MinGW/



Then you have a msys icon on your desktop.

You now double click on this icon.
--> You get a unix-like environment

create a "something.c" file in:
c:\msys\1.0\home\YOUR_USERNAME\

let it contain 

#include <stdio.h>
#include <stdlib.h>

int main()
{
   printf("Hello world\n");
   return EXIT_SUCCESS;
}


Now to compile in c, go to the msys console and type:
gcc something.c -o EXECUTABLE_NAME_HERE

if you want to compile in C++, rename something.c to something.cpp, go to the msys console, and type:
g++ something.cpp -o EXECUTABLE_NAME_HERE

then you can execute it by typing EXECUTABLE_NAME in the msys console.
And you can execute it on windows natively, no problem.


---------------------------------------------------------------------

Setting up a cross-compiler:
Setting up the MinGW Cross Compiler on Debian GNU/Linux

First, install all programs necessary:
```
 apt-get install alien wine mingw32
```

The standard MinGW libraries will probably be incomplete, causing 'undefined symbol' errors. 

So get the latest mingw-w32api RPM and use alien to either convert it to a .tar.gz file 
from which to extract just the relevant files, or to convert it to a Debian package that you will install. 

MinGW Cross Compiler
[http://sourceforge.net/projects/mingw-cross/]("http://sourceforge.net/projects/mingw-cross/")
-->Download - Browse all files
SELECT: [CORE] mingw-cross  	mingw-3.14-3
 Choose:
  	mingw-w32api-3.11-3.fc9.i386.rpm
  	mingw-w32api-3.11-3.fc9.x86_64.rpm
 Download it from its sourceforge download location.

```
alien mingw-w32api-3.11-3.fc9.i386.rpm
rm mingw-w32api-3.11-3.fc9.i386.rpm
dpkg -i mingw-w32api-3.11-3.fc9.i386.deb
```

```
updatedb
locate mingw32 >> MinGWlocations.txt
```
==> i586-mingw32msvc-c++

or 
dpkg --search mingw32
==> i586-mingw32msvc-c++

Cross-compiling:
```
i586-mingw32msvc-c++ greetings.cpp -o greetings.exe
wine ./greetings.exe
```

*********************************
*       START greetings.cpp     *
*********************************
```
#include <windows.h>	// include the Windows API

// Application object which says hello and goodbye
class GreetingsClass
{
	public:
		GreetingsClass() // say hello when object is constructed
		{
			say( const_cast<char*>("Hello World!") );
		};

		~GreetingsClass() // say goodbye when object is destroyed
		{
			say( const_cast<char*>("Goodbye World!") );
		};

		void say(char* chrptr_Message)
		{
			// Use the Win32 function MessageBox to display the message
			// with an OK button and an information icon
			MessageBox(NULL, chrptr_Message, "Greetings", MB_OK | MB_ICONINFORMATION);
		};
};



// WinMain function is the entry point for Win32 programs
int APIENTRY WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow)
{
	GreetingsClass firstInstance;
	GreetingsClass* secondInstance = new GreetingsClass;
	delete secondInstance;
	MessageBox(NULL, "The secondInstance has now been destructed.", "Note:", MB_OK | MB_ICONINFORMATION);
	return EXIT_SUCCESS;
}
```
*********************************
*      END greetings.cpp        *
*********************************

Content of MinGWlocations.txt:
> /usr/i586-mingw32msvc
/usr/bin/i586-mingw32msvc-addr2line
/usr/bin/i586-mingw32msvc-ar
/usr/bin/i586-mingw32msvc-as
/usr/bin/i586-mingw32msvc-c++
/usr/bin/i586-mingw32msvc-c++filt
/usr/bin/i586-mingw32msvc-cc
/usr/bin/i586-mingw32msvc-cpp
/usr/bin/i586-mingw32msvc-dlltool
/usr/bin/i586-mingw32msvc-dllwrap
/usr/bin/i586-mingw32msvc-g++
/usr/bin/i586-mingw32msvc-gcc
/usr/bin/i586-mingw32msvc-gcc-4.2.1-sjlj
/usr/bin/i586-mingw32msvc-gccbug
/usr/bin/i586-mingw32msvc-gcov
/usr/bin/i586-mingw32msvc-gprof
/usr/bin/i586-mingw32msvc-ld
/usr/bin/i586-mingw32msvc-nm
/usr/bin/i586-mingw32msvc-objcopy
/usr/bin/i586-mingw32msvc-objdump
/usr/bin/i586-mingw32msvc-ranlib
/usr/bin/i586-mingw32msvc-readelf
/usr/bin/i586-mingw32msvc-size
/usr/bin/i586-mingw32msvc-strings
/usr/bin/i586-mingw32msvc-strip
/usr/bin/i586-mingw32msvc-windmc
/usr/bin/i586-mingw32msvc-windres
...

---

### Post by Sinkingships7 on 2008-12-06
> **Delever said:**
> [DevC++]("http://www.bloodshed.net/devcpp.html") is what many people use. You can also use VS Express C++, but your program will require small runtime for that. As long as you use only STD library, it's easy, but things get messy if you want to throw some other libraries into the picture. However, I imagine that in your case it will actually be more C than C++ anyway...

C'mon OP, make life easier on yourself. Installing DevC++ through WINE is fast and simple. When it compiles, it will create a Windows-native executable.

---

### Post by WitchCraft on 2008-12-25
> **Sinkingships7 said:**
> C'mon OP, make life easier on yourself. Installing DevC++ through WINE is fast and simple. When it compiles, it will create a Windows-native executable.

interesting. But crappy. that way you cannot use makefiles, so you are forced to use the IDE.

---

### Post by monkeyking on 2008-12-25
> **WitchCraft said:**
> interesting. But crappy. that way you cannot use makefiles, so you are forced to use the IDE.

I found some menu options in devc and code::blocks that should make it possible to use Makefiles. But I couldn't get it to work.

I ended up installing mingw,perl and some unix tools that you always use.
This was included in the Rtools package.
Only needed to change the env path for windows.
Then I could use Makefiles.

But but this was just a std commandline program, no strange graphic libs and so on.

So if you really want to do cross compilation, stick with the basics.

------------
btw just give him the linux exe and the sourcecode,
that ought to make him happy


good luck

---

### Post by WitchCraft on 2008-12-27
You can cross-compile directx applications.

See OpenArena Developer FAQ: [http://openarena.wikia.com/wiki/DeveloperFAQ](http://openarena.wikia.com/wiki/DeveloperFAQ)

[http://www.libsdl.org/extras/win32/common/directx-devel.tar.gz](http://www.libsdl.org/extras/win32/common/directx-devel.tar.gz)

Just uncompress the tar.gz in the mingw directory.

:KS

---

