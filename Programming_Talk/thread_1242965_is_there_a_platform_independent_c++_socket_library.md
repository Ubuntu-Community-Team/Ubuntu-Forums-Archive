---
title: "is there a platform independent c++ socket library and tutorial?"
date: 2009-08-17
forum: Programming Talk
---

### Post by megamonk on 2009-08-17
hi,

im planning to build an open source mmorpg. im pretty good at php, mysql, apache, had experience in 3d using blender, developed minigames (platformers, tile based worlds, wordgames)in flash and im pretty good in math. currently, im learning c++ and im at polymorphism. im a newbie ubuntu convert. im using codeblocksIDE. im a c++ newbie.

my goal is to develop a fully working client/server mmorpg. i will load all assets like characters and maps from the outside of the client. im not a graphics person so ill leave that part to designers. im just going to focus on developing the app (client/server).

my problem is that ive been googling for a week now and i cant seem to find a good tutorial and/or c++ socket library to fit my needs.

heres an explaination of what i need:

i need a c++ socket library that is platform independent and free :P . im always getting winsock or another library that doesnt work on other platforms whenever im searching or a library that is not free. i basically want to be able to create a game client that will work on both linux and windows without changing or creating another set of codes (i dunno if this is really possible but im hoping it is). it doesnt matter if that library is hard to use. im very willing to learn. the server will be on linux.

can anyone please point me to the right direction?

Thanks

---

### Post by dwhitney67 on 2009-08-17
Try Python or SDL Net.

Really though, from what I can recollect the differences between the Win API and the Unix/Linux API are minimal.  Windoze, for some bizarre reason, requires one to manually load a DLL to utilize sockets.

Google some more; I suspect that you are not doing enough leg work.

---

### Post by kknd on 2009-08-17
I've wrote a thin layer last year. You can get it here: [http://svn.tuxfamily.org/viewvc.cgi/oproj_oprojsvn/socket/trunk/](http://svn.tuxfamily.org/viewvc.cgi/oproj_oprojsvn/socket/trunk/)

.

It was tested on MS-Windows (with VS) and on GNU/Linux, but I never really used it, so it may contain bugs.

---

### Post by megamonk on 2009-08-17
> **dwhitney67 said:**
> Try Python or SDL Net.

Really though, from what I can recollect the differences between the Win API and the Unix/Linux API are minimal.  Windoze, for some bizarre reason, requires one to manually load a DLL to utilize sockets.

Google some more; I suspect that you are not doing enough leg work.

i actually considered python for the client/server using Panda3d. however, while researching and considering the tools i need, i realized (i may be mistaken) that python is a bit slower than c++. im making a 3d game so i need very fast execution times. add to the fact that c++ is the de facto standard in making games so i decided to use c++. 

ive been googling for a week now :(. i tried mixing and matching keywords like "socket, c++, tutorial, library, free, game development, API, client/server, chat, etc..." to get results, browsed the pages till the result page reached page 30+ and im still stumped :(.

i actualy found one but it aint free... it uses cygwin :(

---

### Post by skirkpatrick on 2009-08-17
Look at SDL.  Not only will it give you a common networking library but also graphics, audio, etc.  There's even a couple of gaming libraries.

---

### Post by SledgeHammer_999 on 2009-08-17
maybe use the boost(asio) libraries!?!? link->[http://www.boost.org/doc/libs/1_39_0/doc/html/boost_asio.html](http://www.boost.org/doc/libs/1_39_0/doc/html/boost_asio.html)

---

### Post by soltanis on 2009-08-18
Okay. If you are looking for a higher-level library, the other posters here should have given you a good idea -- I'm pretty sure boost has a library for this, and it should be all happy and cross-platform and very nice with C++.

However, the obvious (to me) answer to your question is the Berkeley Sockets API, which is already implemented basically uniformly between Windows, OS X, and Unix spawn. There are a few differences -- very few -- like dwhitney said Windows requires that you manually link another library in (Winsock) and includes a different header file (winsock.h instead of sys/socket.h). It also has a few initialization calls not in common with the Unix interface (wsainit or something or another). These problems you could abstract away in basically one source file, along with other details like connecting and controlling the low-level aspects of a connection.

I know this will look very difficult, and it isn't exactly the most intuitive stuff, but it's pretty good. Look at Beej's guide to network programming; it's actually for C, but since C++ is only C with extras, the code should be compatible. And cross-platform.

Of course, it's a low-level API -- so it's not very gentle.

[http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

---

### Post by megamonk on 2009-08-18
> **skirkpatrick said:**
> Look at SDL.  Not only will it give you a common networking library but also graphics, audio, etc.  There's even a couple of gaming libraries.

sdl will be my next target. for now im going to use glut. im still a newbie in c++ so i dont want to overwhelm myself too much. my prioritiy for now is to produce a custom and stable client/server environment. which will become the backbone of my game.

> **SledgeHammer_999 said:**
> maybe use the boost(asio) libraries!?!? link->[http://www.boost.org/doc/libs/1_39_0/doc/html/boost_asio.html](http://www.boost.org/doc/libs/1_39_0/doc/html/boost_asio.html)

thanks! ive been reading its descriptions, going through tutorial and stuff and it feels very promising. is it really cross flatform? the decription seems a bit too broad. do you have any experience using this?

> **soltanis said:**
> Okay. If you are looking for a higher-level library, the other posters here should have given you a good idea -- I'm pretty sure boost has a library for this, and it should be all happy and cross-platform and very nice with C++.

However, the obvious (to me) answer to your question is the Berkeley Sockets API, which is already implemented basically uniformly between Windows, OS X, and Unix spawn. There are a few differences -- very few -- like dwhitney said Windows requires that you manually link another library in (Winsock) and includes a different header file (winsock.h instead of sys/socket.h). It also has a few initialization calls not in common with the Unix interface (wsainit or something or another). These problems you could abstract away in basically one source file, along with other details like connecting and controlling the low-level aspects of a connection.

I know this will look very difficult, and it isn't exactly the most intuitive stuff, but it's pretty good. Look at Beej's guide to network programming; it's actually for C, but since C++ is only C with extras, the code should be compatible. And cross-platform.

Of course, it's a low-level API -- so it's not very gentle.

[http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

thanks! this is a great tutorial. now i know what kind of protocol is best suited for my game. lots of question in my head got answered just by reading the tutorial.

---

### Post by SledgeHammer_999 on 2009-08-18
> **megamonk said:**
> 
thanks! ive been reading its descriptions, going through tutorial and stuff and it feels very promising. is it really cross flatform? the decription seems a bit too broad. do you have any experience using this?


No I don't have any experience with the Boost libraries. But they are popular with C++ people. And yes they are cross-platform.

---

### Post by Kirienko on 2010-04-15
You could use NetLink Sockets C++ Library.
It is a C++ library, is platform independent and it is very easy to use. It also supports IP6. You can find examples in its website:

[http://sourceforge.net/projects/netlinksockets/]("http://sourceforge.net/projects/netlinksockets/")

[http://netlinksockets.sourceforge.net/]("http://netlinksockets.sourceforge.net/")

Do not confuse this lib with the netLink sockets of the kernel in linux (they are two different things).

I hope this will be useful to you!!

---

### Post by DangerOnTheRanger on 2010-05-02
I would recommend SFML( [http://sfml-dev.org]("http://sfml-dev.org/") ) as I can personally say that it is *way *better than SDL as it has a simpler OO interface, and also has other libraries, such as window management, threading, and sound.

BTW, I don't think you should make an MMO, and be a newbie at C++. You need to make something simpler first.
*Trust me. I've been there, done that. :(*

---

