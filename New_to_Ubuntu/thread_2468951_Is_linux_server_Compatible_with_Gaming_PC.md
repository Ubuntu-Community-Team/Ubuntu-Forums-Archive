---
title: "Is linux server Compatible with Gaming PC"
date: 2021-11-15
forum: New to Ubuntu
---

### Post by saraah34 on 2021-11-15
Hi all, Can yo please tell me Is linux server Compatible with Gaming PC  I want linux server  to run with my gaming pc. every thing available in pc

---

### Post by yancek on 2021-11-15
The question seems too  vague to me.  Gaming server for what, specific games?  Most games are designed to run on windows so indicating what type of game(s) you mean would help.  A server is a server.  I don't do gaming so someone else should be along who will be more helpful.

---

### Post by TheFu on 2021-11-15
No.

Linux is not Windows. They are two different OSes.  Lots of effort has gone into making thousands of games run under Linux, but about 20% will never run under Linux.  About 20% of the top 1000 games run with ZERO issues, on the right Linux OS, with the correct hardware.  There is never any guarantee that any specific game will work on all hardware.

Linux Servers don't have any GUI, so you won't use a mouse at all.  That is a workstation which has a GUI.

**Linus Tech Tips** is a youtube channel for gamers. For the last month, they've been doing Linux gaming stuff.  A few Linux specific episodes:
[https://youtu.be/Co6FePZoNgE](https://youtu.be/Co6FePZoNgE) - Noobs Guide to Linux Gaming
[https://youtu.be/6T_-HMkgxt0](https://youtu.be/6T_-HMkgxt0)  Linux gaming is BETTER than windows?
[https://youtu.be/IWJUphbYnpg](https://youtu.be/IWJUphbYnpg) - Linux Gaming finally doesn't Suck

But Linux isn't Windows.  They are very different OSes with VERY different goals. Many things are better in Linux (finding, installing, maintaining 99% of software) and some are much worse (video editing for non-creators). There are underlying differences which always surprise Windows and MacOS users, so expect about 20% of Windows knowledge to still apply, but the other 80% is different ... even when it appears to be very similar.  It isn't.

If you want to run a gaming server ... like mindcraft or some linux-specific servers, then Linux most definitely **is** better than Windows, but there are always challenges if you want to make a server available over the internet.  A few people, every few months, post about their Linux Game servers being hacked in these forums. Typically, they were extremely new to Unix/Linux and only followed a step-by-step guide to get something working without really knowing anything about security.  Those people tend to get hacked very fast and often lose control of their server running in a VPS somewhere.  Because they didn't have daily, automatic, versioned, backups, there is really only 1 answer - the server cannot be trusted, so it needs to be nuked from orbit. That's the only way to be sure there are tiny tools left buried somewhere that phone home and provide a reverse connection for the "bad guys".

---

### Post by ActionParsnip on 2021-11-15
The server has no GUI so seems a waste to not use a GUI based OS. It also makes gaming work (or are you not wanting a GUI based OS and happy to use command line).

There are also lots of "gaming PCs". Does yours have a make and model? If not then can you please give a specification. Your question is FAR too vague for anyone to say anything definite as there are no definite details

---

### Post by grahammechanical on 2021-11-16
Perhaps you are thinking of having a Linux server machine networked to a Windows Gaming machine. That I should think is possible. But I doubt that a Windows operating system would be able to access files on the Linux server machine. Whereas, a Linux OS can access files on a Windows machine under certain circumstances. Both machines would be able to access the same router/hub without interfering in the operation of the other OS. It will all depend on what you specifically mean by this statement:

> I want linux server  to run with my gaming pc. every thing available in pc

Regards

---

### Post by LokiScarlet on 2021-11-24
If you're asking if a game server on Linux would work with games you're playing on Windows, that's a definite yes, assuming the server application is available for Linux. When you run a game server, the game engine is running on the server and the client. As such, the game server and game client speak the same language, regardless of what operating system they're running on.
If you're asking if you can play games on the server version of Ubuntu, that would be a no. You potentially could, but you would want to install the desktop version. Many games are available for Linux these days, and thanks to Valve furthering development of WINE with their fork known as Proton, even the Windows games are pretty easy to run now.
If you're asking whether you'll have trouble running on your hardware, we'd need more details about what components make up your computer. Just about everything works these days, some things requiring more work than others. Anything with an AMD GPU will work fine without any proprietary shenanigans, but NVidia can be a challenge for newcomers.

---

