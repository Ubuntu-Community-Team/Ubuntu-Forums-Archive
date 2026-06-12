---
title: "Cpu info in C"
date: 2007-08-18
forum: Programming Talk
---

### Post by scourge on 2007-08-18
So I wrote a simple parallel search with pthreads for my chess program (Sloppy). It works beautifully, and uses both of my 2 cores.

Is there any way to find out how many cpus/cores are available to my program, maybe something in the GNU C library? Or do I have to scan /proc/cpuinfo or something? Right now I have to run ./sloppy -t 2 to use two threads, but it would be great if my program could figure out the optimal number of threads by itself.

---

### Post by moma on 2007-08-18
Ask Sysconf what the system limits are:  
[http://www.gnu.org/software/libc/manual/html_node/Sysconf.html](http://www.gnu.org/software/libc/manual/html_node/Sysconf.html)

And example:[COLOR="RoyalBlue"]
    #include <unistd.h>

    int numCPU  = sysconf(_SC_NPROCESSORS_CONF);[/COLOR]
----------------------------------------

E.g I have seen it in x86info tool among many other programs. 

This example shows how to get the source code for x86info tool. 
$ [COLOR="SeaGreen"]mkdir $HOME/source[/COLOR]
$ [COLOR="SeaGreen"]cd $HOME/source[/COLOR]
$ [COLOR="SeaGreen"]sudo apt-get source x86info [/COLOR]

$ [COLOR="SeaGreen"]cd x86info-1.18[/COLOR]

Search for "sysconf" 
$ [COLOR="SeaGreen"]grep -R sysconf * [/COLOR] 

It's so easy.
----------------------

PS. Linux MCE (Media Edition) 0704 released. 
[Watch the amazing demo....]("http://video.google.com/videoplay?docid=2176025602905109829&q=0704&total=4842&start=0&num=10&so=0&type=search&plindex=0")

---

### Post by scourge on 2007-08-18
> **moma said:**
> Ask Sysconf what are the system limits:  
[http://www.gnu.org/software/libc/manual/html_node/Sysconf.html](http://www.gnu.org/software/libc/manual/html_node/Sysconf.html)


Works perfectly. Thanks a million. I knew it shouldn't be too difficult. I managed to stick with pure ANSI C for a long time, but now I'm way past that point.

---

