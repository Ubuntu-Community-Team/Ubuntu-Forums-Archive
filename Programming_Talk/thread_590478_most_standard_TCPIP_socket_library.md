---
title: "most standard TCP/IP socket library"
date: 2007-10-24
forum: Programming Talk
---

### Post by dumbsnake on 2007-10-24
Hello,

    I'm trying to write a server that responds to HTTP requests.  I'd like to work from TCP/IP and implement the actual parsing of the HTTP packets.  I wrote a similar program a few years back on windows, but I haven't used that excuse of an operating system in over a year now.  I have found <sys/socket> but it seems that operates at the IP level.  As much fun as implementing my own version of TCP is... I'm sure there is a better solution.

    I develop in C++, but I don't generally care for libraries written in C++ (unless they actually do a really good job of it).  Also, it seems system libraries are always in C anyway.  Ideally, linux has a standard library that is present on every system that implements TCP sockets.  I'm not sure why I can't find it, but if anyone knows what it is called and how to use it let me know.  Ideally I'd work from a low level interface where I get a system file.

    I hope I have been clear and I appreciate any help.

---

### Post by gradedcheese on 2007-10-24
I guess I don't fully understand your question... <sys/socket.h> operates at the TCP socket level... it's exactly what you'd use to handle HTTP.  It's the POSIX socket() as you'd expect to have.

---

### Post by dumbsnake on 2007-10-25
Hm... ok, I didn't realize sys/socket did TCP/IP.  Thanks for the clarification.  I'm surprised I've had so much trouble finding the documentation I needed, but I think I found something to help me get it working.  Thanks for the help.

---

### Post by hecato on 2007-10-25
perhaps helpfull the 2 first results?? [http://www.google.com.mx/search?q=socket+programming](http://www.google.com.mx/search?q=socket+programming)

---

### Post by dumbsnake on 2007-10-25
wow, thanks....   I was looking in ALL the wrong places.  In retrospect I feel sort of stupid for not finding that.  Thanks for the help!

---

### Post by gradedcheese on 2007-10-25
```

sudo apt-get install -y manpages-dev manpages-posix-dev
man 2 socket

```

:)

---

