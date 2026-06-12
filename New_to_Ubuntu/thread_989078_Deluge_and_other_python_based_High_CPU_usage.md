---
title: "Deluge and other python based High CPU usage"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by paulo21 on 2008-11-21
!!!!!***This post is not intended to criticize Deluge or its programmers.***!!!!!!

My computer is an old athlon Xp 2600+ with 2Gb DDR, Geforce FX5200 on an ASUS mobo (A7V400-SE) running Xubuntu Hardy 8.04, kernel 2.6.24.21-generic.


I use deluge to download torrents and I liked it pretty much. It's a nice program.

The point is a curious behaviour of Deluge and some other python based programs when minimized.

When not minimized, deluge is CPU hungry, it consumes about 60% of it. 

But the best part is that when minimized it consumes as much as 2% of CPU!

I noticed the same behaviour-lower than 2% CPU usage in other python based software running on Ubuntu or Xubuntu, both Hardy 8.04.

Anyone could explain me what is all about.

Thanks in advance.

Paulo Bulcão.

---

### Post by bscbrit on 2008-11-21
If it is using significantly more CPU power when displayed than when it is minimised then it suggests that the CPU is having to do a lot more work producing the display.  This is not, in itself, unusual for any program but if it is making the program unusable then it is possibly a poor design.

Years ago, when I first started on computers (Nascom 1 with 4KB (yes KB!)  of programmable memory and a 2MHz CPU), programs were designed to optimise the use of every bit.  But CPU power and memory storage have increased dramatically.  Today, it is more cost effective (i.e. cheaper) to use higher level languages and software development frameworks and tools to write programs, plus there are many more advantages.  Despite compiler optimisations, if the programmer makes a bad design decision it might work on his own high powered computer but become less usable on less powerful computers.  But, even with a good design, there is always an overhead with using such frameworks and tools.  In your case, your machine is not that badly spec'ed, and I would have expected the program to work more efficiently than it does.  I run Ubuntu on machines with far less power than yours quite satisfactorily - but I do not use Deluge.  My only suggestion is to try another downloader if the CPU usage is a problem.  If it is something that you can live with, then you might just have to get used to watching the pretty displays of CPU usage in SystemMonitor.:-)

---

### Post by kostkon on 2008-11-21
> **paulo21 said:**
> !!!!!***This post is not intended to criticize Deluge or its programmers.***!!!!!!

My computer is an old athlon Xp 2600+ with 2Gb DDR, Geforce FX5200 on an ASUS mobo (A7V400-SE) running Xubuntu Hardy 8.04, kernel 2.6.24.21-generic.


I use deluge to download torrents and I liked it pretty much. It's a nice program.

The point is a curious behaviour of Deluge and some other python based programs when minimized.

When not minimized, deluge is CPU hungry, it consumes about 60% of it. 

But the best part is that when minimized it consumes as much as 2% of CPU!

I noticed the same behaviour-lower than 2% CPU usage in other python based software running on Ubuntu or Xubuntu, both Hardy 8.04.

Anyone could explain me what is all about.

Thanks in advance.

Paulo Bulcão.
That's Python for you. 2% is not much for a Python torrent app, I think. Although, I don't know about the 60% you are saying, it seems too high. I have to test it myself.

Which version of Deluge do you use?

---

### Post by Michael.Godawski on 2008-11-21
Perhaps you have to minimize the amount of connections like in this thread?
[http://ubuntuforums.org/showthread.php?t=317068](http://ubuntuforums.org/showthread.php?t=317068)

---

