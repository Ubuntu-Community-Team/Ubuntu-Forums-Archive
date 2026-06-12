---
title: "Cross platform (Linux/Windows) FIFO/Pipe in C?"
date: 2008-05-23
forum: Programming Talk
---

### Post by cjbailey1 on 2008-05-23
I have searched through various forums and been googling for quite a while but have yet to come up with a sensible answer.

I am writing a cross-platform program which requires two seperate programs with simple communication between them.  Under linux I would use 'mkfifo' with 'read' and 'write' commands, but this functionality doesn't seem to be available under Windows ](*,).  To make the code as simplistic as possible I have been trying to find a way to open a pipe under windows (the only one I've found so far is 'CreateNamedPipe') and then be able to use the same commands to read and write to it as I can in linux (be they 'read' and 'write', 'fread' and 'fwrite' or whatever).

I don't wish to be burdened with using CygWin as I don't want the users (a school in this case) to have to install it on each machine.  I am currently using GTK+ (for GLADE) to create the user interface, which means they will have one more dependancy than they need!

I realise that I could simply write my own 'create', 'open', 'read' and 'write' routines which then call the relevant rountines to execute the command on each system, but there must be a tidier way to do it!

Also, if there are any good forums/resources out there for cross-platform C programming then I'd be glad to be pointed at them :lolflag:

Many thanks,
   Chris.

---

### Post by randallecook on 2008-05-24
I recommend creating a TCP/IP socket connection between the two machines. On the unix side, you can use the socket descriptor in read and write, of use fdopen to use fread and fwrite. On Windows, you might need Winsock code to create the socket connection, but the read/write/fread/fwrite calls should work.

If you want cross platform everything, you might want to look at [Qt]("http://trolltech.com/products/qt"), or [ACE]("http://www.cs.wustl.edu/~schmidt/ACE.html"), or the [Boost]("http://www.boost.org/doc/libs/1_35_0/doc/html/boost_asio.html") [Asio]("http://asio.sourceforge.net/") library.

If you want to read about interprocess communication like this, the standard text is [Unix Network Programming, Volume 2]("http://www.kohala.com/start/unpv22e/unpv22e.html"). Good luck.

Randall

---

### Post by cjbailey1 on 2008-05-24
Many thanks for the reply, I'm well aware of creating network connections under both systems, what I'm asking is about (and I'm not always very good at explaining what I want) is interprocess communications on the SAME MACHINE.

The code I am writing will need to be compiled for use on both Windows and Linux machines as the school has a suite of each.  The code is modular and because of some of the libraries used cannot be done with threading (there is a weirdness within the GTK+ libraries).  I am merely trying to simplify my code as much as possible within the main routines so I have as much code cross-compiling as I can.

---

### Post by smartbei on 2008-05-24
You can use network connections to create connections between processes on the same machine - just use the loopback interface (ip 127.0.0.1). If you create a process that listens on a certain port, another process (on the same machine, or another - it doesn't matter) can connect to this port. As a bonus, these two processes can in the future be on different machines.

---

### Post by cjbailey1 on 2008-05-24
The previous poster had got me thinking about doing that, I need to check with the school that they won't be running the program on any non-networked machines (there are a few machines without network cards in!) but I guess this would be a workable solution.  It should also mean I can reuse code from elsewhere rather than rewriting things.

The reason my mind immediately jumped to a fifo/pipe is that's how I'm used to working (high-speed, embedded, real-time linux).

Thanks for the replies :)

---

### Post by NormR2 on 2008-05-25
Java might be a solution. I've written programs that use sockets to communicate on the same machine between separate processes. 
I don't think there is a need for a network card to use the localhost (127.0.0.1) address.

---

### Post by Lau_of_DK on 2008-05-25
> **cjbailey1 said:**
> (there are a few machines without network cards in!) 
Thanks for the replies :)

If you need something cross-platform that can communicate even w/o networking, why dont you mount the windows partition under linux and simply share info through a log file on the filesystem, where both parties can watch for changes?

/Lau

---

### Post by DavidBell on 2008-05-25
> **cjbailey1 said:**
>  but this functionality doesn't seem to be available under Windows ]

Which specific functions are missing from the windows version? My reading of the docs is you can use CreateNamedPipe with PIPE_ACCESS_DUPLEX mode to get fifo, so would just have to set up a few functions in #ifdef LINUX .... #elif defined WINXP ... etc.

wxWidgets also has a wxPipe class that should be cross platform, you could have a look at how they go about it.

DB

---

### Post by geirha on 2008-05-25
> **cjbailey1 said:**
> 
I don't wish to be burdened with using CygWin as I don't want the users (a school in this case) to have to install it on each machine.  I am currently using GTK+ (for GLADE) to create the user interface, which means they will have one more dependancy than they need!

Actually, you don't need cygwin to run a program compiled in cygwin. You just need to have cygwin1.dll in windows' dll-path or in the same directory as the executable (and any other dlls you might have linked against of course).

---

