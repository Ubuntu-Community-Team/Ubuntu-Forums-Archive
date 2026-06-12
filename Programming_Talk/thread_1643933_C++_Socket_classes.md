---
title: "C++ Socket classes"
date: 2010-12-12
forum: Programming Talk
---

### Post by roadkillguy on 2010-12-12
Does anybody know of any good c++ socket classes? I've been searching and searching to no avail.  UDP is what I'm looking for.

Thanks!

---

### Post by dwhitney67 on 2010-12-12
C++ itself does not offer a suite of classes to support sockets.  You do, however, have options available to you.

1.  You can develop your own socket classes;
2.  You can use Boost's asio package;
3.  Or use some other 3rd-party library that offers such.

I'm not sure if your goal is to learn how to implement a (UDP) socket interface, or merely use some pre-existing interface that obfuscates the nitty-gritty details of dealing with sockets.


P.S.  Long-ago, I went with option 1 above.  Let me know if you wish to use it.

---

### Post by roadkillguy on 2010-12-12
I'm actually looking to make a game of mine multiplayer.  I've been able to get SDL_net working, but I don't want to have to use the SDL graphics library just for simple sockets. D:  If your class has the basic functions such as bind, resolve host, open, etc. I would be willing to implement them into my little wrapper class.

---

### Post by dwhitney67 on 2010-12-12
Ah, SDL_net... that was the other package that I forgot to mention earlier.  A lot of folks use it because it is available for Windoze and Linux.

My Socket library, which is still a "work in progress", is useful only under Linux.  Of course, it supports the basics: TCP, UDP, Raw Sockets, Multicasting.  Nowadays, I merely tinker with creating example client/server apps.

Anyhow, I've attached the library for your convenience.

---

### Post by roadkillguy on 2010-12-12
Yeah, cross platform would be nice.  Do you know if SDL_net can be cross compiled to windows using mingw?  Maybe you could drop me libSDL_net.a or something...

EDIT: Nevermind! I got SDL_net cross compiling.  Thanks for the help!  It turns out you can sometimes rename SDL_net.lib to libSDL_net.a and have mingw cross compile it for windows.

---

