---
title: "Need guidance on developing a c++ program for Ubuntu and Windows"
date: 2009-12-06
forum: Programming Talk
---

### Post by diablo75 on 2009-12-06
I'm not a programmer, but a good friend of mine is.  A couple years ago he created a little app for me to help me conduct remote desktop sessions with clients who needed help with their computers.  It is basically a launcher for TightVNC and would execute the necessary commands to initiate reverse VNC connections between me and them with one click of a button, so it was very user friendly.  He created this software using Visual Studio 2005, which I didn't really like because there is a lot of overhead that comes with that particular language so he wants to take a crack at creating it with Visual C++.  In addition, we'd both like to find out what it would take to port this software over to Linux to be distributed as a deb file.   But neither of us know the first thing for developing for Linux.

As far as Linux goes, the only dependency that I know the program would require is x11vnc, as it's what I use in Ubuntu to establish reverse VNC connections.  You just simply execute "x11vnc -connect [server address]:5500" and that was basicly it.  It worked pretty much the same way in Windows with TightVNC, with a slightly different syntax but the with the same results.  Having the user create a shortcut for this isn't exactly difficult, but I'd rather make it easier for them to do by just downloading a deb (or exe in Windows), installing a small launcher app along with x11vnc (or whatever vnc program we settle on for Windows Vista/7) and run the necessary command for them with a single click.  

How difficult would it be to port an app like this over from Windows to Ubuntu if it's written in C++?  How do you create a deb package?

---

### Post by utsavgupta on 2009-12-06
VS 2005 uses the .NET architecture. I had attended MICROSOFT DEV CON (Microsoft Developer's Conference) which was held at my college, the speaker told us that Microsoft is planning to develop a .NET platform for the Linux operating system.

Now if that happens then your VS 2005 code should run on Ubuntu.

However if you want to develop softwares in C++ for Linux then you can do so. There are some differences between MS C++ and G++. I guess quite a few changes are required to port your code from VS 2005 to G++.

VS 2005 uses the apis present in the .NET platform to draw its GUIs and VS 6.0 used MFC, however you have this fantastic GUI toolkit called Qt, it is a cross platform toolkit and it's free. So a program written in C++ should work in G++ as well as in VS 2005, 2008.


Cheers,

Utsav Gupta

---

### Post by diablo75 on 2009-12-06
> **utsavgupta said:**
> VS 2005 uses the .NET architecture. I had attended MICROSOFT DEV CON (Microsoft Developer's Conference) which was held at my college, the speaker told us that Microsoft is planning to develop a .NET platform for the Linux operating system.

Now if that happens then your VS 2005 code should run on Ubuntu.

However if you want to develop softwares in C++ for Linux then you can do so. There are some differences between MS C++ and G++. I guess quite a few changes are required to port your code from VS 2005 to G++.

VS 2005 uses the apis present in the .NET platform to draw its GUIs and VS 6.0 used MFC, however you have this fantastic GUI toolkit called Qt, it is a cross platform toolkit and it's free. So a program written in C++ should work in G++ as well as in VS 2005, 2008.


Cheers,

Utsav Gupta

Hey that sounds great!  Thanks for pointing me in the right direction.  Qt sounds like what we're looking for.

---

### Post by SledgeHammer_999 on 2009-12-06
You can also use [wxWidgets](www.wxwidgets.org)

---

