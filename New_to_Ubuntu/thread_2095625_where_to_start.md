---
title: "where to start"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by themartuigan on 2012-12-17
so ive been doing alot of searching over the past few days. trying this and that. looking here and there. im still stuck. i dont know what to do. 
im having a hard time figuring it all out. theres too many options. 

im trying to do a couple things at once here. 
first of all i want to find the most simplest unix i can. this is so i can learn. and im not talking simple as in install and surf the web. im talking simple as in one file. small. the core. the minimalist amount. something for me to build up. but my biggest problem i suppose is needing a good manual to go beside that. unfortunately my options are limited to this computer and some encyclopedias. 
this is not a discussion about why i have to live so far away from some place that offers the ease of obtaining some things so please dont ask. i simply do not have access to a library, or a beginners course. 
i have the internet, need there be more?


where do i start? 
if there is another unix that i should try, i will gladly. 
at this point. i want to start small. and learn every thing. from the very beginning. to the very end. i want to start with the core kernel and an understanding of what it is and where to go from there. 
step by step from beginning to end. 

there is so much to learn. but there must be a beginning....

where do i start ?

---

### Post by audiomick on 2012-12-17
First of all, I dare say you mean Linux rather than Unix. They are similar in some ways, but are in fact two different system. Look for then in the Wikipedia, perhaps.

Regarding this
> **themartuigan said:**
> im talking simple as in one file. small. the core. the minimalist amount. something for me to build up.

As far as starting simple goes: the Linux kernel is very small. I believe it is just one file. As far as I know, though, it deosn't actually do anything productive until you start adding modules to it.

There is such a thing as a minimal Linux install. I believe Ubuntu was offering one at one point, but I am not sure. As I understand it, that is a "working" Linux system that doesn't have any programs in it. You can then build it up to include what you want. 

Having said that, I would strongly suggest starting with a complete distribution. That will give you a working and useful OS with a set of programs, and will most likely install and run with very little trouble. Use this to learn how Linux works, how the file system is set up, how to use the command line and such like. On any Linux install, you can always work in a terminal to use commands. You can, when you are up to it, even boot it without having the Desktop running so you have a pure command line environment to learn in.

I think it would be very complicated trying to learn all that stuff whilst trying to build an OS from scratch. Once you have your head around those basics, though, you are much better set up to approach the complex subject of what you need in a working OS, how to put it together, and how to get it installed so it will run.

In your position, I would start with something like Ubuntu that is intended to be user friendly, then progress to Debian, which Ubuntu is built up on. Debian requires more effort from the user to get a complete install. From there, you could go to Debian minimal ( I think they offer such a thing) or maybe something like Arch Linux
[http://en.wikipedia.org/wiki/Arch_linux]("http://en.wikipedia.org/wiki/Arch_linux")

---

### Post by chadk5utc on 2012-12-17
Not sure exactly what your looking for or want out of it. Ubuntu is for Linux about as easy as it gets for most people. You mention Unix but Im not sure that there is really an easy unix.
 If your searching for mini distro's there are tons which will install in around 50-100 mbits???

---

### Post by ibjsb4 on 2012-12-17
I agree with "audiomick", stick with an already built distro until you know more about how to build your own and especially when you have a better understanding of software packages and how to use them.  A couple of thing that could help you:

#1  [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

#2  [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

#2  will give a brief description; what a package depends on; what it will install; what it will break and so on.

---

### Post by snowpine on 2012-12-17
This site helped me a lot when I was learning Ubuntu: 

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

A good place to begin learning about Linux is to boot a Live USB/DVD of Ubuntu and try using it for some of your familiar daily tasks (browsing, word processing, listening to music, etc).

---

### Post by Cheesemill on 2012-12-17
The smallest Ubuntu installation you can get is by using the Mini CD to install (mini.iso).
This will give you a system that boots into a command line and nothing else. Even this will install hundreds of files though, you cannot have a bootable installation made up from just one file.

[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

---

### Post by Impavidus on 2012-12-17
I started with Unix. When I came to university the machines closest to the student cantine were X terminals plugged into a Solaris server five floors up. They had such low resolution black-and-white monitors that you were basically stuck to the command line. I didn't have to do any administrative tasks, of course, but by digging into the system, reading all kinds of configuration files, doing everything on a text interface (even browsing the web) I learned how the system worked. When I installed my first Ubuntu machine six years ago I was quite familiar with the design of the system and the command line interface. Unix and Linux are very similar from the user's point of view.

I think that was the easy way to start.

You can't study a tree by looking at a log. So if you want to study a tree, don't start with the heartwood at the centre of the trunk. Start with the leaves and the flowers, which are easy to study and of which you can see where they're attached to, and once you understand them start digging for the roots. It's just the same with computers. Start with the user interface, dig into the file system, read those configuration files in /etc, have a look at all background processes running and you'll start to understand Linux. It just takes some time.

Only use your administrative privileges when you know what you're doing. When not using those privileges it's hard to break your system, so be curious. I never broke my system. Maybe I was too cautious (in contrast to my user name). Ask google, read man pages, open any strange file you can find on your system in a text editor. Most are text files anyway. You will get some feeling for what ought to be possible on your system and what would be a breach of Linux's design philosophy. I think one of the best thinks about Linux is that it doesn't hide the internals of the system from the user's eye, so that you can understand its inner workings. I never understood Windows XP and never used the later versions.

I wish you good luck getting to know Linux. And come back here for any questions you have. It's best learning from people who can tell you what's going on. I still learn new things every week.

---

### Post by Zill on 2012-12-17
> **themartuigan said:**
> ... i want to start small. and learn every thing. from the very beginning. to the very end. i want to start with the core kernel and an understanding of what it is and where to go from there. 
step by step from beginning to end...
I have to admire your ambition!  I have been using several flavours of GNU/Linux for around ten years now and still have *so* much to learn - maybe I'm just a slow learner. ;-)

There is a lot of good advice in this thread and I can only include my advice to start off with a "user friendly" full distro, such as Ubuntu, rather than making things hard for yourself by starting with the "core kernel" or a minimalist system.

As you use Linux, you will then learn as you go and will expand your knowledge steadily.

Read (and participate in!) these forums regularly as they are a mine of useful information.  Don't forget that "Google is your friend" and others have often experienced previously any problem you may hit so there is no need to reinvent the wheel.

---

### Post by audiomick on 2012-12-17
> **Impavidus said:**
> I started with Unix.... I still learn new things every week.

That is a really good post.
:popcorn:

---

### Post by LiamOS on 2012-12-17
A very small UNIX clone is minix. It's pretty simple, and you could get it up and running in virtualbox easily. It's a bit... of a drag if you get a bit used to linux first, but it does what it's meant to do well, which is to be small, stable and educational. 

If you want to learn more about linux as a whole, I recommend Gentoo linux, and then dabbling with Linux from Scratch. Gentoo teaches you a lot about maintaining and setting up a linux installation, and Linux from Scratch teaches you how to get a minimal system from scratch. 


Then again, Linux from Scratch on its own may just be what you're looking for.

---

### Post by chadk5utc on 2012-12-17
Funny you should mention "Minix" as it was used in the creation of Linux
[http://en.wikipedia.org/wiki/History_of_Linux](http://en.wikipedia.org/wiki/History_of_Linux)

---

### Post by offgridguy on 2012-12-17
> **audiomick said:**
> that is a really good post.
:popcorn:
+1

---

