---
title: "C++ Multiplatform sockets"
date: 2011-07-16
forum: Programming Talk
---

### Post by Pierrick584 on 2011-07-16
Hello, i'm starting to work onto a game, and i'm horribly stuck on the networking part, i tried the panda3d client-server in the documentation, well, seems there's only python documentation on it... tried asio, cant find a good tutorial that actualy compile, tried... about 5 or more other sockets library, none work/got good documentation.

Realy, i'm stuck for like two years on the multiplatform sockets problem, anybody out there can possibly help me? in any way with any library that is multiplatform (if mac is excluded, i wont cry)

Thanks in advance to anyone who will try to help.

---

### Post by karlson on 2011-07-16
> **Pierrick584 said:**
> Hello, i'm starting to work onto a game, and i'm horribly stuck on the networking part, i tried the panda3d client-server in the documentation, well, seems there's only python documentation on it... tried asio, cant find a good tutorial that actualy compile, tried... about 5 or more other sockets library, none work/got good documentation.

Realy, i'm stuck for like two years on the multiplatform sockets problem, anybody out there can possibly help me? in any way with any library that is multiplatform (if mac is excluded, i wont cry)

Thanks in advance to anyone who will try to help.

If you are looking for a multiplatform Socket Abstraction library take a look at [http://www1.cse.wustl.edu/~schmidt/ACE.html](http://www1.cse.wustl.edu/~schmidt/ACE.html)

I am not sure why you had issues with ASIO.  Boost's tutorial page worked pretty well for me.

---

### Post by Pierrick584 on 2011-07-16
I did have a look at ACE.. i guess i dint check in the good section in "documentation" yet, i dont see where a tutorial for the basics.

As of the official boost asio documentation, i find the tutorial not clear at all... dunno, cant get **** working with it, and i doupt i'm the problem, as i remember a few years ago when i used to be on windows, found a winsock tutorial and got a basic chat client/server up in a very short time (aint talking of copy/paste)

---

### Post by cipherboy_loc on 2011-07-16
A friend recommend the boost libraries for a cross platform project. Like you, I had issues getting it working, but I remember finding some tutorial somewhere (sorry, was an old project -- don't remember what the links were). 


Cipherboy

---

### Post by karlson on 2011-07-16
> **Pierrick584 said:**
> I did have a look at ACE.. i guess i dint check in the good section in "documentation" yet, i dont see where a tutorial for the basics.


ACE gives you various patterns for implementing network communicating software, so you might want to either invest in or check out at the library(if you can) of these:

[http://www.riverace.com/acebooks/index.htm](http://www.riverace.com/acebooks/index.htm)

---

### Post by Pierrick584 on 2011-07-17
I would definitively be up of buying one of these books, i do learn alot by books, if i actualy manage to get some ACE code compiling before though... and i do have some trouble on that

---

### Post by GeneralZod on 2011-07-17
"The Boost C++ Libraries" is a good, free book on Boost, and has a sample client and server implementation:

[http://en.highscore.de/cpp/boost/asio.html#asio_networkprogramming](http://en.highscore.de/cpp/boost/asio.html#asio_networkprogramming)

---

### Post by Pierrick584 on 2011-07-17
> **GeneralZod said:**
> "The Boost C++ Libraries" is a good, free book on Boost, and has a sample client and server implementation:

[http://en.highscore.de/cpp/boost/asio.html#asio_networkprogramming](http://en.highscore.de/cpp/boost/asio.html#asio_networkprogramming)


Thanks, thats definitively a good link, beside i still have trouble after reading it, it does not seem complete enough for what i wana do... witch isint that complex realy, i'm barely looking to have simple tcp and udp connection, and send strings and int

---

### Post by SaberToothSlug on 2012-01-27
[Pierrick584]("http://ubuntuforums.org/member.php?u=1145035"), since this an older post I thought I would check in with you before posting anything lengthy.  I was impressed that you had been pursuing this issue for two years and was wondering if you had anything working with Panda yet?

---

