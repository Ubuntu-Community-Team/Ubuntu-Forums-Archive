---
title: "What do I need to compile C projects for Windows"
date: 2007-02-14
forum: Programming Talk
---

### Post by brashquido on 2007-02-14
Hi All,

Sorry for this very newb question, but I couldn't see my specific question been asked before.
I am very green to Linux and will be using Ubuntu for almost all my desktop needs from here on in (due mainly to DRM in Vista).

Several servers I look after are Windows 2003 Server and what I'd like to be able to do now that I'm using Linux is to compile Windows DLL's for several PHP projects for use on my Windows Servers. I take it I'll need gcc and a few other tools (A GUI would be really great), but as I know nothing of C programming is there anything else I'd have to do to compile source files from the PHP site for use on Windows 2003 Server / IIS?

---

### Post by shrimphead on 2007-02-24
The best thing to use would be bloodshed Dev-C++ ([http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)) it's a free(as in beer and speech) IDE for C and C++ development under windows. It has the MinGW compiler suite built in and is a very nice IDE.

Your other option I suppose would be Visual Studio? personally I prefer Dev-C++ when I have to work on windows

---

### Post by runningwithscissors on 2007-02-24
> **brashquido said:**
> Several servers I look after are Windows 2003 Server and what I'd like to be able to do now that I'm using Linux is to compile Windows DLL's for several PHP projects for use on my Windows Servers. I take it I'll need gcc and a few other tools (A GUI would be really great), but as I know nothing of C programming is there anything else I'd have to do to compile source files from the PHP site for use on Windows 2003 Server / IIS?
This could be hairy.
If you mean you need to compile Windows DLLs on Linux for deployment on Windows machines, you'll need to build a cross-toolchain.
Most distros make this possible by including easily deployable packages in their repos for this purpose. I don't know what the package is called on Debian (probably mingw32). Still, you'll need libraries that your code links to, to be compiled using the cross toolchain, and in the case of windows-specific libraries for which code isn't available, that would be difficult.

Ooh, I found a simple howto.
[cl1x0r](http://www.hamilton.ie/paul/mingW32_howto.html)

---

### Post by lnostdal on 2007-02-24
[http://ubuntuforums.org/showpost.php?p=2088439&postcount=5](http://ubuntuforums.org/showpost.php?p=2088439&postcount=5)

edit: well, the guide in the post above me here gives some more details about how one can get up the windows-libraries that you might need for your task

---

### Post by j_g on 2007-02-25
Ugh. As someone who has done lots of windows programming, especially DLLs, and is now doing Linux programming, let me give you a good tip.

The quality of Linux development tools is extremely poor compared to Windows counterparts. Do not develop Windows software on Linux. Do your Windows software on Windows. You can't beat Microsoft Visual C++ 6.0 for C/C++ development. Now that MS has kind of abandoned it for .NET, you may be able to pick up a used copy cheap. The compiler comes with standard C libs, all Windows includes files and libs (ie, what you get in the Windows SDK), a good IDE with built-in editor and debugger, project management, etc. You'll never need to touch a makefile if you use VC 6.0, and that includes doing a DLL as well. The one product includes everything you need to make a Windows DLL in C/C++.

---

### Post by gaillard on 2007-02-25
Surely with the tremendous linux development there are some good tools?  Or are you just saying that the ones for windows under linux are poor?

---

### Post by Mirrorball on 2007-02-25
You can develop Windows software on Linux, because gcc has been ported to Windows. For j_g: you don't need to write Makefiles or use the autotools with Dev-Cpp. It's an IDE for Windows that uses gcc.

---

### Post by j_g on 2007-02-25
I'm saying that if you want to develop Windows DLLs, then you just can't beat getting a copy of Microsoft Visual C++ 6.0. It has everything you need in the one package, and its ease of use in writing/compiling/linking/debugging/packaging Win32 software is unrivaled.

The cost of obtaining a copy of MS Visual C++ 6.0 and MS Windows is negligible compared to the headaches you'll be spared trying to get something else to do Win32 software, particularly on Linux. If you'd like a URL to a bunch of Win32 DLLs I've personally written, and hold copyrights to, so that you know that I speak from experience in talking about Win32 DLL software, just let me know. I'm not just speculating here based upon how I _think_ things are. I'm speaking from years of experience writing Win32 DLLs.

---

### Post by lnostdal on 2007-02-25
right .. do not mind j_g

* doing development on linux is absolutely great!
* creating dlls on win32 using mingw or cygwin is not a problem

brashquido: feel free to PM me if you need help getting started with any of this .. i'd be glad to help

edit:
but .. without me knowing anything about what your goal is here; there might be better ways to extend PHP than by writing C "plugins"

---

### Post by gaillard on 2007-02-25
what I want to know is how I was supposed to know that the command for mingw was something like i386-... or i586-...

the package didn't say that was it and how do I get the man page if I don't know the command!

Their site said it was something like mingw32, is it just the debian packages that are like that, because it should be on the wiki then =)  New users like me have trouble with the simple stuff you know...

---

### Post by lnostdal on 2007-02-25
ok, to figure out what executable "commands" a package installs you can do something like this:

```

root@ibmr52:~# dpkg -L mingw32 | grep bin
/usr/bin
/usr/bin/i586-mingw32msvc-g++
/usr/bin/i586-mingw32msvc-c++
/usr/bin/i586-mingw32msvc-gcov
/usr/bin/i586-mingw32msvc-gccbug
/usr/bin/i586-mingw32msvc-cpp
/usr/bin/i586-mingw32msvc-gcc
/usr/bin/i586-mingw32msvc-gcc-3.4.5
/usr/bin/i586-mingw32msvc-cc

```

---

### Post by Mirrorball on 2007-02-25
> **j_g said:**
> The cost of obtaining a copy of MS Visual C++ 6.0 and MS Windows is negligible compared to the headaches you'll be spared trying to get something else to do Win32 software, particularly on Linux.
Add to it the headache of having to switch between Linux and Windows constantly and the cost of Windows itself, if he doesn't have it. He said he uses Linux and he will probably want his PHP modules to work on his Linux installation too. Will his MS Visual C++ project be easy to compile on Linux? Probably not.

---

### Post by gaillard on 2007-02-25
> **lnostdal said:**
> ok, to figure out what executable "commands" a package installs you can do something like this:

```

root@ibmr52:~# dpkg -L mingw32 | grep bin
/usr/bin
/usr/bin/i586-mingw32msvc-g++
/usr/bin/i586-mingw32msvc-c++
/usr/bin/i586-mingw32msvc-gcov
/usr/bin/i586-mingw32msvc-gccbug
/usr/bin/i586-mingw32msvc-cpp
/usr/bin/i586-mingw32msvc-gcc
/usr/bin/i586-mingw32msvc-gcc-3.4.5
/usr/bin/i586-mingw32msvc-cc

```

Well that is quite useful, thank you very much... I thought about grep but I didn't find it just using find, thanks for the help!!

---

### Post by lnostdal on 2007-02-25
:) .. you can view what files a package installs via synaptic also by the way .. just find the package (search), right-click and select "properties" -- and then you'll find them under "installed files"

---

### Post by j_g on 2007-02-26
> Add to it the headache of having to switch between Linux and Windows constantly

I dual-boot, or boot up two networked systems. It's no problem. In fact, it takes much less time to boot into Windows than it typically does to work out problems with Linux dev tools (especially if you're using them to do something esoteric like make Win32-only software).

> and the cost of Windows itself, if he doesn't have it. He said he uses Linux and he will probably want his PHP modules to work on his Linux installation too.

He's talking about making a Win32 DLL. A Win32 DLL is not a native Linux format. He can't use it on Linux anyway. And he'll need Windows assuming he'll want to test the DLL so he knows whether his code actually works (unless he plans to do testing on some machine at a different location. I really don't see how this could possibly be less of a "headache" than having a test machine at the same location).

Ultimately, it all depends upon how much his time and sanity is worth to him. I say, if he values his time, and wants to avoid real "headaches" in doing Win32 software, he should do what the vast majority of Win32 developers have already discovered to be the easiest and most efficient approach -- avail himself of MS Dev tools. (Actually, you can free versions of .NET dev systems).

---

### Post by Mirrorball on 2007-02-26
> **j_g said:**
> I dual-boot, or boot up two networked systems. It's no problem. In fact, it takes much less time to boot into Windows than it typically does to work out problems with Linux dev tools (especially if you're using them to do something esoteric like make Win32-only software).
For me it would be a problem. I normally do a lot of things at the same time and I would have to interrupt them to boot into Windows. Making Windows software is not esoteric, if you expect to compile it with gcc.
> **j_g said:**
> He's talking about making a Win32 DLL. A Win32 DLL is not a native Linux format. He can't use it on Linux anyway.
A Windows dll is equivalent to a Linux shared library. He could compile hiscode as a Linux shared library and a Windows dll, then he could use it on Linux too, no need to boot into Windows when he wants to develop something using his PHP module.
> **j_g said:**
> And he'll need Windows assuming he'll want to test the DLL so he knows whether his code actually works (unless he plans to do testing on some machine at a different location [...]).
He says his module is for a Windows 2003 server. He will probably test it there.
> **j_g said:**
> I say, if he values his time, and wants to avoid real "headaches" in doing Win32 software, he should do what the vast majority of Win32 developers have already discovered to be the easiest and most efficient approach -- avail himself of MS Dev tools.
OK, you've given him your opinion and now I'm giving him mine. gcc works fine either on Linux and on Windows and allows him to create a library that works on both systems, with the additional advantage that he doesn't need to boot into Windows to write software.

---

### Post by j_g on 2007-02-26
> For me <dualboot> would be a problem.

Normally, it takes more than a couple minutes to develop something. It's not like I boot into Windows for 5 minutes, and then boot back into Linux.

Ironically, I've just finished writing Linux shared lib versions of 3 Windows DLLs I wrote. I boot into Windows, and stay there until I finish coding/debugging the Windows DLL. I fully test it under Windows. When the code is working, then I boot into Linux, and add the Linux-specific code (and #ifdef's to block out the Windows specific things). Then, I test it under Linux. Typically I'll test a preliminary version to verify that my approach works under both systems, so I don't get too far on a wrong path.

I use Visual C++ 6.0 to make the Windows version, and gcc to make the Linux version. Just because it's the same codebase doesn't mean that you have to use the exact same compiler/linker/libs. Not only is that a myth, but it actually produces code that isn't as good as choosing tools that are optimized for a given platform. I choose tools that make my work easier and more efficient, and are better supported upon their given platforms.

I start with the Windows version because I find MS dev tools to be superior to Linux offerings. So the initial fleshing out of the code, and testing, is done under Windows with Visual C++. That makes a little less work to do on Linux.

> A Windows dll is equivalent to a Linux shared library. He could compile his code as a Linux shared library and a Windows dll, then he could use it on Linux too[/code]

Well, he'll use the .so file, not the Windows .dll file, under Linux. Of course, these are two entirely different files. There is no such thing as a universal binary "dynamic link library" between Win32 and Linux.

[quote]no need to boot into Windows

Um, there's a matter of actually running something to verify that it does indeed not crash horribly, or exhibit aberrant behavior. Yes, he does need to boot into Windows. One should never assume that something works without actually trying it.

As one example, in my Win32 DLL, I had two threads that communicated by passing messages between windows. A Win32 window handle is good between threads. Now when I ported that code to Linux, and used the pthread library, I assumed that an X Window display device handle would be good between threads (because I had not found any documentation that specifically stated otherwise). It turns out this isn't the case. I had to make sure I did an XOpenDisplay from each thread, and each thread had its own handle to the display. Now, if I had simply used gcc on Windows to make a Linux .so, ran the Windows DLL, and assumed that the Linux version would work just because the Win32 version did, I would have had a nasty surprise. Fortunately, I  tested my work under both systems, so I was able to do a little redesign of the code to accomodate both Win32 and Linux before I got so far with the coding that it would have been a major hassle to rework.

There's a big difference between telling someone that you can theoretically do something a certain way, and advising someone to take a given approach based upon personal experience.

---

### Post by lnostdal on 2007-02-26
vmware-player works great when doing this kind of stuff  .. no need to dualboot .. might need to pop in some extra memory though; 1GB is what i consider minimum when doing this

btw .. about threads .. there is a pthread-port to win32 .. while i have no idea what you're working on it might be suitable .. you get more portability between linux and win32

a different approach is using winelib which is portable between linux and win32

another thing to consider, but again depending on what you're doing - is using gtk+ (instead of win32-gui or xlib-gui) which is also portable between linux and win32

yet another approach is using cygwin which has an implementation of X  ... a "more native" X that doesn't depend on the cygwin dll also exists: [http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming)

edit:
oh, and about what i can confirm works great:

* using vmware-player instead of dual-booting: works great ... i _never_ dual boot now (i use sshfs so i can edit my windows-files under linux .. then execute the compilation "remotely" using ssh .. it's totally transparent and vmware/winxp is minimized at all times .. seen distcc btw.?)
* threading: i wrote a couple of classes that wrapped linux-pthreads and win32-threads in a simple portable api .. so i haven't tried pthreads-win32 extensively
* winelib: never tried this approach
* gtk+: works great under both win32 and linux .. portable and easy .. no need for vc++6.0 .. i basically mirror the toolset and setup i have on linux; which ofc _is_ excellent (when you're not a MS-n00b)
* X under win32: never tried it (well, i've used applications that use/depend on it many times, and they work great .. but i haven't developed applications that do this (i use gtk+, rendering "natively" or via cygwin - instead))

---

### Post by runningwithscissors on 2007-02-27
I find development on Windows nasty.

I usually don't know where my libraries are, where to specify linker and compiler options, how the build system works, etc. etc. on Win.

It's too complicated.
(Yes, I don't use IDEs on Linux either)

And I've tried developing with both, the Win32 API, and Xlib. As far as windowing code goes, I can say that each is as cryptic as the other.

---

