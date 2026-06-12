---
title: "Free C++ Compiler for Windows"
date: 2007-10-20
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-20
I am looking for a free Compiler for Windows XP. I'm not sure what a good one is. It would be nice if it was portable also.

I was looking on [portableapps.com]("http://portableapps.com/") but couldn't really find anything.

Thanks in advance.

---

### Post by dwhitney67 on 2007-10-20
devC++

---

### Post by aks44 on 2007-10-20
> **TreeFinger said:**
> I am looking for a free Compiler for Windows XP. I'm not sure what a good one is.

- [MinGW]("http://www.mingw.org/") is GNU g++ for Windows (currently based on g++ 3.4.5, while 4.2.1 is available as a beta)

- Microsoft's compiler is the de-facto standard on Windows. It has some shortcomings from a language "purity" perspective, but it produces damn good optimized binaries. [MSVC 8 (Express edition)]("http://msdn.microsoft.com/vstudio/express/visualC/default.aspx") is freely available for download, although with a few limitations (no resource editor IIRC, and certainly a few other details).

- Borland has a free C++ compiler too, but really you shouldn't bother with it unless you *need* to integrate with Delphi code. It is... well... outdated and has way too much proprietary extensions.


> **TreeFinger said:**
> It would be nice if it was portable also.

Don't dream too much, we're talking about C++ compilers here... ;)

---

### Post by DougB1958 on 2007-10-20
A couple of my students fell in love with Code::Blocks this past summer. I have no personal experience with it beyond looking over their shoulders and seeing that it looks like a fairly typical IDE, but they thought it was easy to install and use, and easy to port a fairly big project to.

---

### Post by aks44 on 2007-10-20
> **DougB1958 said:**
> A couple of my students fell in love with Code::Blocks this past summer. I have no personal experience with it beyond looking over their shoulders and seeing that it looks like a fairly typical IDE, but they thought it was easy to install and use, and easy to port a fairly big project to.

Code::Blocks is just that: an IDE. You must provide it with a compiler backend (MinGW, GCC on Linux, MSVC7, BCC55 and a few others). However IIRC there is one download option to have it prepackaged with MinGW.

---

### Post by LaRoza on 2007-10-20
For Windows, Dev-C++, [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

For Windows, non-portable, also Dev-C++, [http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

You if you set your path variables, you can use g++ through the command line, just like Linux. If you get Vim for Windows, you can have the total *nix experience!

---

### Post by TreeFinger on 2007-11-04
How do I run a program I just compiled and keep the console open? When I run a simple hello, world program from dev-C++ after compiling the window just flashes open and then closes with out me being able to read any output?

---

### Post by Paul820 on 2007-11-04
Tell it to wait for a keypress:
> std::cin.get();
Or if anything is left in the buffer, use two of the above.

---

### Post by TreeFinger on 2007-11-04
> **Paul820 said:**
> Tell it to wait for a keypress:

Or if anything is left in the buffer, use two of the above.

Thanks, that requires the user to hit enter. Is there a way to do in the way of, 'press any key to continue?'.

---

### Post by Paul820 on 2007-11-04
In C++ i don't think there is a way. In C, you can use getchar() function.

---

### Post by TreeFinger on 2007-11-04
OK, thank you.

---

### Post by TreeFinger on 2007-11-04
How the hell do I display line numbers in Dev-C++

---

### Post by LaRoza on 2007-11-04
Tools->Editor Options->Display->

---

### Post by NathanB on 2007-11-04
Sizable list of options here:

[http://www.thefreecountry.com/compilers/cpp.shtml](http://www.thefreecountry.com/compilers/cpp.shtml)

---

### Post by Lux Perpetua on 2007-11-04
> **Paul820 said:**
> In C++ i don't think there is a way. In C, you can use getchar() function.getchar() also requires pressing enter. It's because no characters actually enter the input stream until the user presses enter. Actually, I don't know a way to get an unbuffered keypress without using termios or curses, but I don't have much Windows programming experience.

---

### Post by LaRoza on 2007-11-04
> **Lux Perpetua said:**
> Actually, I don't know a way to get an unbuffered keypress without using termios or curses, but I don't have much Windows programming experience.

In Windows, 

[php]
#include <conio.h>

getch();
[/php]

---

### Post by j_g on 2007-11-04
Waiting for any key press in Windows is simple:

```
HANDLE fh;
const char AnyKey[] = "\r\nPress any key to close the window...\r\n";
char buffer;
DWORD count;

fh = GetStdHandle(STD_OUTPUT_HANDLE);
WriteFile(fh, &AnyKey[0], sizeof(AnyKey) - 1, &count, 0);
fh = GetStdHandle(STD_INPUT_HANDLE);
ReadFile(fh, &buffer, 1, &count, 0);
```

---

