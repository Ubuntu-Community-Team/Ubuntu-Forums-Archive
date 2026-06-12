---
title: "Ask for a documentation to port a windows program to linux?!"
date: 2010-06-23
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-23
Hi all!
 
I'm using ubuntu 9.04;
I have a large project in windows that I want to "port" it in linux.
It uses IPC mechanism "Shared memory" and also "Critical Section" APIs in windows, but unfortunately I have no good reference to change these windows APIs to their equivalent in linux?
 
Is there a comprehensive documentation or reference for this issues?
I mean a table containing the equivalent APIs or systemcalls in windows and linux!
 
For example, what's an alternative for the "InitializeCriticalSection" API in linux?
Or an alternative for "CRITICAL_SECTION" structure?
Or even an alternative for "RegOpenKeyEx", although we don't have registry in linux!!
 
TIA.

---

### Post by nvteighen on 2010-06-23
As it's a project of yours and you say it's large, I guess the best way to port it is using the Wine API. Porting from an OS specific API to another's is in no way a trivial task, specially when it's from Windows. Think about it: Windows GUI API is integrated into thw whole Win API, but in GNU/Linux you have to choose from Qt, GTK+, Motif, etc. depending on what Desktop Environment you target to and other criteria. Other differences are, e.g. the lack of a System Registry... in GNU/Linux we use text files, either at /etc or at the user's home, so it boils down to standard textfile reading procedures using the C or C++ Standard Library (or whatever language you're using)... that would mean to change the structure of any code of yours using the Registry API to something completely different.

The Wine API (which is a GNU/Linux native reimplementation of the various Windows APIs except DirectX) may not be perfect and you may still have to do some changes, but they'll certainly not be as much as you'd have to do by porting it manually. 

And don't be fooled by the argument that Wine API is "cheating". It's a legimitate way of porting something to GNU/Linux... it's just a reimplementation of an API, as the GNU C Standard Library is.

---

### Post by Zugzwang on 2010-06-23
In a nutshell, you won't find any such comprehensive piece of documentation for such issues. The reason is that Linux' structure is fundamentally different to Windows' one.

In Linux, there are functions provided by the kernel and there are the libraries. The latter provide functionality on top of the kernel function. All these parts are written by different author teams and thus do not have a unique documentation. Also, for some tasks there are multiple ways to go. For example, in Windows, there's an API for making windows and the like. In Linux, you would never do that directly but rather "speak" to GTK, WxWidgets, QT, or TK (or some possibilities I forgot about).

On the other hand in Windows, you see one *big* API, whereas this is chunked among the libraries in Linux. On top of that, there are things that are simply handled differently in Linux. You named one example: the registry. In Linux, the registry resides in files. The system-wide stuff is in "/etc", the user-specific stuff in directories/files starting with "." in their home directories. On top of that, to give you registry-like functions for user-wide settings, KDE and Gnome have their APIs.

As far as your critical section stuff goes, choose one of the multi-threading libraries. They all provide support for critical sections, but there's no 1-to-1 mapping. For this reason, people are normally advised to use portable libraries for all aspects of a program, because then, no rewriting has to take place and all special commands are encapsulated. This however on the other hand means that you will not be able to use the specialities of some OSses.

---

