---
title: "Equivalent of package java.net in GNU C library"
date: 2009-11-04
forum: Programming Talk
---

### Post by rbaleksandar on 2009-11-04
Hi, guys. :)


  So far, so good. I have made (omho) a big progress in C. The thing I want to do now is to sent a small-sized file (for example a text-file) vie network (sockets, IPs blabla). I want to be able to recieve such too (two-way-transfer so to say). Now in Java this is done with the **package java.net**, which handles the work with sockets, ports, IPs etc(example: the InetAddress-class which represents IP adress and how it can be handled). The thing is a want to read some data, put it inside a file (sort of a report) and send it via network to another machine. Can someone tell me at least where to look since I'm not an expert in Java, but when it comes to implementing something like that in C...well, you get the point I hope. :D


Thanks a lot! Any explanations and suggestions are welcome. ;) 


PS: I was thinking in going through a part of the Wireshark-source but damn that's so complicated. :D

---

### Post by SunSpyda on 2009-11-04
No standard socket libraries exist for C, only 3rd party ones. BSD sockets for UNIX/UNIX-like OSes, and WinSock2 for Windows.

In all honesty, porting between the two is easy. You just have to swap close() for closesocket(), include the ws2_32.lib library (Or your implementation equivalent), and use WSAStartup()/WSACleanup(). There are a few other oddities, but nothing major.

Something like this may be simpler in a higher-level language like a .NET language, JVM language, or one of the other popular dynamic languages like Ruby and Python. They all have portable socket APIs.

There may be some 3rd party who provide portable socket libraries for C, but I personally program sockets on both platforms, & I stick to the native libraries myself.

---

### Post by rbaleksandar on 2009-11-04
Thanks for the quick reply.

  1)I want it to be in C. I'm learning this language because I need it. ;)
  2)I'm interested in multiplatform-develompent. Can you give me an advice what should I do if my (yet) very basic program has to work under Linux, Windows, Unix etc. Later I might try transforming it into C++-program (not very experienced there too) by using Qt-GUI. But that's not in the near future, so I'll stick to basic terminal program written in C.


Thanks in advance. :)

---

### Post by Simian Man on 2009-11-04
If you insist on using C, you can look into the SDL_net library which just wraps up the native socket library for each platform.

---

### Post by SunSpyda on 2009-11-04
> **rbaleksandar said:**
> Thanks for the quick reply.

  1)I want it to be in C. I'm learning this language because I need it. ;)
  2)I'm interested in multiplatform-develompent. Can you give me an advice what should I do if my (yet) very basic program has to work under Linux, Windows, Unix etc. Later I might try transforming it into C++-program (not very experienced there too) by using Qt-GUI. But that's not in the near future, so I'll stick to basic terminal program written in C.


Thanks in advance. :)

No problem :) Yeah, C is a superb language, but it does lack libraries at times (For good reasons).

Now, I know nothing about Qt, but I know it has a portable socket library... which means you could (theoretically) write a portable program by writing the GUI & sockets in Qt, & the rest in other Qt components & the standard C library.

Qt is C++ though, so C++ will need to be learned. So hey presto, after working through Qt & C++, a portable, networking, GUI program will be possible (There's ALWAYS complications though :( ).

If you wish to deal with the native socket libraries, you could get ugly with the preprocessor. This technique will result in issues, especially if your trying a OO approach.

I say learn C++, then Qt to do socket programming. Or, even easier, specialize onto a certain platform, then 'become portable' at a later date.

---

### Post by rbaleksandar on 2009-11-04
Well, I'm planning on learning C++ (since I need this and that for building a basic Qt-app), but right now I don't have enough time. :( I'll check the SDL_net library, which Simian Man suggested (thanks!). Probably will give it a try to do this for Linux/Unix and than think about making a port for Win for example. Found I couple of very nice tutorials and just found out that there are explanations (very basic or too complicated omho) in the GNU C Library Documentation.


Thanks you very much for helping me. Really appreciate that. ;)

---

### Post by SunSpyda on 2009-11-04
> too complicated

Socket programming isn't that hard conceptually, it's just the evil libraries you have to deal with in C that make it evil ;)

---

### Post by rbaleksandar on 2009-11-04
:D Doesn't matter. It's still pain in the a*se. ;) But learning something like that is very useful in the future (for me especially :)).

---

### Post by SunSpyda on 2009-11-04
Let me guess... you want a CS career? :p

Yeah, I imagine sockets & C would be useful for that.

---

### Post by rbaleksandar on 2009-11-04
Yes... I'm working on a small project now. It consists in reading form a F/T (force/torque) sensor, sending the infomation (as described above), receiving it inside a program and analysing it (the Qt will be needed for visiual thingies :)). I'm planning on a career in Humanoids and Intelligence Systems Laboratories (Robotic- and Med-stuff) at my university and as you can see - understanding and being able to build network-oriented applications is a must. :D But for now I just want to do a little experimenting to see how it works in C (I think I'm starting to fall in love with this language especially because I'm able to use it on microcontrollers :KS ).


PS: Who does things like these, if he/she's not interested in a future in CS? LOL

---

### Post by SunSpyda on 2009-11-04
> PS: Who does things like these, if he/she's not interested in a future in CS? LOL
Me :p

I really don't want a career in CS, but I know this sort of stuff anyway :/

I'm great at writing whatever programs I want, but I can't do this sort of thing to demand (I've tried and I did it successfully, but it was boring as hell from my POV).

We'll just beg to differ ;)

---

