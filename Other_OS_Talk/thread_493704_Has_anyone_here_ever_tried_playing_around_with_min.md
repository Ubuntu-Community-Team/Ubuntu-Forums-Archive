---
title: "Has anyone here ever tried playing around with minix 3"
date: 2007-07-06
forum: Other OS Talk
---

### Post by swoll1980 on 2007-07-06
Just wondering what it's like/capable of. Linus Torvalds seemed pretty fond of it. just wonder what your expierience with it was like.

---

### Post by jrusso2 on 2007-07-06
I don't think you would be happy with it as a desktop there is not a lot of applications for it.

---

### Post by bchaffin72 on 2007-07-06
While the developers are working to add more practical functionality to it, it is not where GNU/Linux is yet. That being said, I have used different versions of Minix in the past and found it to be decent for what it is. More seems to be planned for the future to make it more suitable for everyday use.

---

### Post by swoll1980 on 2007-07-06
Whats the difference between Unix and Linux is it more professional? less user friendly? or what? I know Minix uses a micro kernel does Unix? I know Linux is a monolithic kernel. I understand the differences as far as the kernel space architecture vs. the user space architecture. but what are the differences in functionality?

---

### Post by H3g3m0n on 2007-07-06
Linux is a UNIX like system, in reality there are no UNIX operating systems around as UNIX was actually the name of an operating system made years ago by AT&T but now days UNIX clones are generally put under the category UNIX. Linux, BSD, Solaris, OSX, etc are all classified as such.

[http://en.wikipedia.org/wiki/UNIX](http://en.wikipedia.org/wiki/UNIX)

In reality most functionality comes from the userspace tools that run, as such a BSD or Solaris system can look and act exactly the same as a Linux system, there is also a project called Nexenta which is making a GNU/Solaris distro designed to be just like Ubuntu but running on Solaris instead of Linux. There are also distrobutions that are using the FreeBSD kernel with GNU userspace tools such as Debian GNU/kFreeBSD which is probably the most complete (there was also 2 Gentoo versions for OpenBSD and FreeBSD but they  never really got developed).

BSDs use their own userspace tools, under a license that only says you must give credit if you use the code (compared to Linux's GPL that says you must also give back the code).

Solaris have their one userspace tools again, under a CDDL licence which is Sun's proprietary but open source license (they are apparently going to GPLv3).

All the userspace tools are designed to emulate the functionality of SysV UNIX so they are compatible across platforms but there are differences, for instance GNU has the -- standard for named command line parameters rather than a single dash for letter parameters so scripts written this way arn't compatible, but since GNU keeps the letters around so you can run scripts from other systems. 

Most of the difference between the systems come from their design, Ubuntu is aimed at being more userfirendly, and compared to most other systems Linux itself is more userfriendly due to the common way userspace tools are setup across distros. Solaris is more for enterprise level systems, its not very user friendly since its assumed people know what the hell they are doing

Linux for instance has colour highlighting when you do an 'ls', its on by default but you can manually force it with 'ls --color', FreeBSD doesn't have this on by default but you can use 'ls -G' and alias it in your shells startup scripts. Solaris just doesn't support colour for ls, but you can install the Linux (technically GNU since Linux is the kernel) version of ls with the colour highlighting.

Devices are also different across systems, while they all have a /dev directory the names of the devices are different and what hardware is supported is different. Linux generally has better hardware support although FreeBSD had better wifi for awhile (maybe still does). /dev/hda doesn't exist on a Solaris system, they use an entirely different naming scheme

---

### Post by init1 on 2007-07-06
> **swoll1980 said:**
> Just wondering what it's like/capable of. Linus Torvalds seemed pretty fond of it. just wonder what your expierience with it was like.
Fond? I thought the early versions of linux actually ran in minix. 
I tried minix 3, but couldn't install it. I am not sure if it recognizes my HD, but if it does, I don't   know the /dev/ syntax.

---

### Post by Fri13 on 2008-11-05
> **swoll1980 said:**
> Whats the difference between Unix and Linux is it more professional? less user friendly? or what? I know Minix uses a micro kernel does Unix? I know Linux is a monolithic kernel. I understand the differences as far as the kernel space architecture vs. the user space architecture. but what are the differences in functionality?

The difference is that **Linux kernel is the OS**, while the microkernel is not the OS alone. 

Monolith kernel is OS, what idea is to run complete OS in one address-space. The Monolith OS has two great features, it is easy to code and it is very fast. But downsides are that an bug in any part of OS; driver, OS service or kernel itself, crash the OS and the whole software system top of OS. And other bad side is that maintaining a monolith OS gets harder what bigger the OS grows. Thats why Linux got modular structure after 2.2 version and it was not anymore a macrokernel (one giant blob).

Microkernel-structured OS idea is that OS is sliced to parts and the kernel runs alone in kernel-space, while the sliced OS servers are located to the userland and those runs on protected process with kernel.  And normal applications connects to the OS servers in userland, example of a filesystem, a network-protocols, device drivers and a scheduler. And OS servers then executes their tasks. Bad sides of microkernel structured OS is that speed is not great, because it is very slow to transferr information between kernel space and userland. But good sides are, that one OS server or driver what crash, does not crash the OS or the software system top of OS either. 

When you compile your driver on Monolith OS, it is compiled against exact kernel version. When you compile the kernel, you need to compile all the drivers and other modules for new kernel, so you need to compile the whole OS for kernel change. (Do not mistake the OS and the software system or development platform to same!). It is same as you would need to compile all the software on your system, when you update your OS. Not so good thing...

On microkernel-based OS, you can compile the kernel alone rest from the OS servers. Or any other OS module (server) without need to think the kernel. It is just like you would update applications in your software systems, you dont need to compile browser if you update a music player.



In short:

Linux (a Monolith kernel) = the Operating System
Microkernel + OS servers = the Operating System
Linux + GNU != Operating System
Linux + GNU = Operating System + Development Tools
Linux + GNU = Development Platform

GNU/Hurd = GNU Operating System
GNU/Solaris = Solaris
Hurd/Solaris = Depends what OS servers the Hurd microkernel use.

**And here are the few links for that... from OS developers and computer science teachers**. 

[http://tinyurl.com/532kb8](http://tinyurl.com/532kb8) 
[http://tinyurl.com/mum9x](http://tinyurl.com/mum9x)
[http://tinyurl.com/qhuhg](http://tinyurl.com/qhuhg)
[http://tinyurl.com/3uaq48](http://tinyurl.com/3uaq48)

Most important thing to learn is that **there is not a such OS as GNU/Linux**... GNU project has not yet got their own OS working. Linux was developed with GNU tools. And Linux evolved to be a complete OS (not just a small kernel). Stallman is bretty angry about this and tried to protect the GNU project with it's own political religion.

So again and in short terms... Linux, the kernel, is the Operating System because it is a monolith kernel and not a "just a kernel", what it would be if it would be a microkernel (= not alone a OS).

The Computer Science is very clear and simple about the definition of Operating System. 

Example of Ubuntu, it is the software system, what includes the Linux Operating System, GNU development tools and basic system libraries and lots of different application programs, like commandline tools, Xorg, Gnome desktop environment and it's applications (Gnome is part of GNU!), Ubuntu theme, icons and own configuration settings by Canonical. Ubuntu is lots more than Operating System. It is full Software Product from commercial company.

---

### Post by SunnyRabbiera on 2008-11-05
I never really tried Minix though I know without it there would be no Linux

---

