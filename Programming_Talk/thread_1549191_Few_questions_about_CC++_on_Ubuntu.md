---
title: "Few questions about C/C++ on Ubuntu"
date: 2010-08-09
forum: Programming Talk
---

### Post by Cha0sBG on 2010-08-09
Hello dear Ubuntu experts, i installed Ubuntu not long ago ( ~ Week ) and i have some experience in Windows programming with c++ so i wanted to ask: What is the general difference in c/c++ programming on windows and Ubuntu? Are the APIs the same or completely different from one another. Any help or suggestions from where to start will be great. Currently i stumbled upon the NetBeans IDE and i think i will use that for my future code. Well that's about it, waiting for your response.

---

### Post by Bachstelze on 2010-08-09
Depends what kind of programs you want to write. The C and C++ libraries are standardized, so as long as you stick with the standard, they're the same. The OS APIs are obviously not.

---

### Post by Cha0sBG on 2010-08-09
What exactly do u mean by standard ? Any example of standard and non-standard APIs would be great ":)

---

### Post by Bachstelze on 2010-08-09
[http://en.wikipedia.org/wiki/C_standard_library](http://en.wikipedia.org/wiki/C_standard_library)
[http://en.wikipedia.org/wiki/C%2B%2B_standard_library](http://en.wikipedia.org/wiki/C%2B%2B_standard_library)

---

### Post by Cha0sBG on 2010-08-09
Aha, so that means the functions like CreateProcess etc wont work? Any development resources for the ubuntu ones ?

---

### Post by dv3500ea on 2010-08-09
The Windows API will not work on Linux.
Instead there is the [POSIX library]("http://en.wikipedia.org/wiki/C_POSIX_library").
If you used GUI libraries in Windows, they may/may not work in Linux.
Cross platform GUI libraries, such as [WxWidgets]("http://www.wxwidgets.org/"), [GTK]("http://www.gtk.org/"), [QT]("http://qt.nokia.com/"), [SDL]("http://www.libsdl.org/") etc will work but the Windows GUI API won't (is it win32.h?)

---

### Post by Cha0sBG on 2010-08-09
I was wondering what is the equivalent to Windows.h in Ubuntu? Or just WinUser.h for the var types like HWND , HANDLE etc ?

---

### Post by Simian Man on 2010-08-09
> **Cha0sBG said:**
> I was wondering what is the equivalent to Windows.h in Ubuntu? Or just WinUser.h for the var types like HWND , HANDLE etc ?

Don't ask what is the *exact* equivalent of ___.  Ask how can I accomplish ___.

Those Windows types like HWND and so on are just typedefs for integers most of the time and nothing like that is really used for Linux.  There is no one header file that pulls in so many things as Windows.h.  And the closest thing to CreateProcess is fork.  But it's a little diffrent since CreasteProcess takes like a dozen arguments and fork takes none.

If you say what you want to do, people will be able to help you with it.

---

### Post by dv3500ea on 2010-08-09
> **Cha0sBG said:**
> I was wondering what is the equivalent to Windows.h in Ubuntu? Or just WinUser.h for the var types like HWND , HANDLE etc ?

Ah, so it is the Windows API that you've been using.
The API will be completely different - so you will have a big learning curve.

I'm not familiar with the Windows API (I don't know the function of Windows.h or WinUser.h), but in Linux, the low level OS stuff is done in the C POSIX Library. GUI stuff is handled separately.

Low level GUI programming can be done using [xlib]("http://tronche.com/gui/x/xlib/introduction/header.html") . You will probably want to use a higher level GUI toolkit (such as GTK).

---

### Post by Cha0sBG on 2010-08-09
For the GUI stuff maybe i'll use QT4 since it's cross platform. So now i have to see how to do all other stuff in ubuntu.

---

### Post by Bachstelze on 2010-08-09
> **Cha0sBG said:**
> For the GUI stuff maybe i'll use QT4 since it's cross platform. So now i have to see how to do all other stuff in ubuntu.

FWIW, GTK is cross-platform too.

---

### Post by trent.josephsen on 2010-08-09
"C/C++" is a myth.  Choose one or the other.

---

### Post by Bachstelze on 2010-08-09
> **trent.josephsen said:**
> "C/C++" is a myth.  Choose one or the other.

So one may not do both? Interesting. Just today, I worked on a C and a C++ project. Death penalty for me?

---

### Post by nvteighen on 2010-08-09
The Windows API is a very monolythic one... In GNU/Linux people like to be free to combine stuff they like however they like (of course, you have to make it work!).

Following the "UNIX Tradition", GNU/Linux usually uses 1 library for 1 single task ("usually"... because you'll see Qt isn't like that, but because of historical details I won't get into here). As most of them are shared libraries that are loaded only once in memory, the cost of having a single executable be linked to several libraries is very little. But it also adds clarity: you know that for task X you need library Y and if there's a bug, you know where to investigate (always start looking at your code before filing a bug report on the library ;))... Also, it makes stuff more reusable.

So, what people usually need is:

1. The C or C++ Standard Library (the one defined by the respective international standard... For C, this includes stuff like printf, fopen, malloc, free, i.e. all the very basic functions you get from stdio.h, string.h, stdlib.h, etc... For C++, everything under the std namespace).

2. POSIX... This is a bit tricky because different POSIX functions are placed in different shared libraries. These functions are mainly to interact with the GNU/Linux system itself... Think of it as the nearest thing to a "GNU/Linux OS API".

3. GUIs: As you'll learn, the GUI system is separate from the OS... so, you don't get access to GUIs from the system but from libraries that are independent of it. You can choose among several different ones, but the two "big guys" are GTK+ (the one used by default by the GNOME project) and Qt (the ones used by default by the KDE project). As all graphics are managed by an intermediate layer called the X Window System, as long as a library is based on X (all are...), you can use Qt on GNOME or GTK+ on KDE, although it may look bad.

---

### Post by vikas.sood on 2010-08-09
> **trent.josephsen said:**
> "C/C++" is a myth.  Choose one or the other.

I write both. Its only the difference of what you think of the programming problem. refer to the oldest book that discusses trade offs.

---

### Post by anewguy on 2010-08-09
gcc and g++, plus I would install build-essential.  From there, as people have mentioned, things are very different from a GUI'd perspective.  I've used GTK for a cross-platform linux(ubuntu)/windows program with no problems.  I have some code I could email you if you'd like to see how it works (it's a merged bunch of code from about 3 or 4 different programs that I made into 1 program to do the same function, so only the GTK part is original code - the rest is modified or extremely highbred code from the other programs to work with GTK).  I find it easier to create a GUI'd app using GTK then going through the "zillions of things" you need to do to do the same thing in Microsofts' C/C++ tools (maybe that has changed since the last time I tried it).

Dave

---

### Post by trent.josephsen on 2010-08-09
> **Bachstelze said:**
> So one may not do both? Interesting. Just today, I worked on a C and a C++ project. Death penalty for me?

No, but I notice you don't say "I worked on a C/C++ project". ;)

I didn't mean to imply that one may not use both; only that they are different languages.  The phrase "C/C++" is misleading because it implies more similarity between the two languages and programming disciplines than exists.  I know of no other languages that are so often conflated and confused.

My point being that asking a question about two different languages in the same breath is likely to earn less specific and helpful advice than (a) choosing a language and asking questions about it or (b) describing a problem and asking for language advice.

---

### Post by SpinningAround on 2010-08-09
This tutorial is quite nice, list the equivalent method in linux for a few methods in windows.

[http://www.ibm.com/developerworks/systems/library/es-MigratingWin32toLinux.html](http://www.ibm.com/developerworks/systems/library/es-MigratingWin32toLinux.html)

---

### Post by worksofcraft on 2010-08-10
lol wut?!
you should always use glade for gui. It even ports to windows I heard!

---

