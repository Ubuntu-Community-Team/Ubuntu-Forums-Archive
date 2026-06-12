---
title: "Why Compile sources?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-11-13
I've been getting a bit better at compiling software from sources using the Terminal.  I only tried a few small games, and they installed perfectly.

I want to know, is there a reason why does Linux compiles from source to install software?  Linux is the only OS I know that does this, Windows you use an installer, or a .deb package in Ubuntu.  Not to mention software sometimes won't compile because I might be doing something wrong.

I'm not complaining or trying to offend anyone, but it just has me wondering why some software is like this.

---

### Post by iponeverything on 2008-11-14
Compiling gives you platform independence. i.e. your not confined to i386.

Also, because because the underling libraries change quite often -- this allows you not to have to create a new binary release for every update to a distro.

---

### Post by Skripka on 2008-11-14
> **LinuxFox said:**
> I've been getting a bit better at compiling software from sources using the Terminal.  I only tried a few small games, and they installed perfectly.

I want to know, is there a reason why does Linux compiles from source to install software?  Linux is the only OS I know that does this, Windows you use an installer, or a .deb package in Ubuntu.  Not to mention software sometimes won't compile because I might be doing something wrong.

I'm not complaining or trying to offend anyone, but it just has me wondering why some software is like this.

Because distributing source code is a SURE fire way of getting programs to people on ANY platform--without the need to spend server space with RPM, DEB, and ALL the other linux flavors as well etc pacakges-- and then you also have to worry about architectures for each of those packages: i386 and amd64 and PPC and...etc etc.  It is more of a pain, and makes things being kept up-to-date on the user-end more difficult, but for the one owning the server space it saves space and effort making sure each package is compiled correctly.

---

### Post by iaskedalice09 on 2008-11-14
I think it's ridicuously fun to compile from source. Though that's just me! :-)

---

### Post by Skripka on 2008-11-14
> **iaskedalice09 said:**
> I think it's ridicuously fun to compile from source. Though that's just me! :-)

It is fun, so long as things compile correctly...when cmake stars spitting gibberish at you though-it is rather off-putting.... :mad:

---

### Post by LinuxFox on 2008-11-14
> **Skripka said:**
> Because distributing source code is a SURE fire way of getting programs to people on ANY platform--without the need to spend server space with RPM, DEB, and ALL the other linux flavors as well etc pacakges-- and then you also have to worry about architectures for each of those packages: i386 and amd64 and PPC and...etc etc.  It is more of a pain, and makes things being kept up-to-date on the user-end more difficult, but for the one owning the server space it saves space and effort making sure each package is compiled correctly.It's a universal thing.  I didn't even know it worked on a wide range of platforms, I thought once a program was made, it could only work on the OS it was made for (Windows works on Windows, Linux works on Linux, etc).

iaskedalice09, I agree.  It was fun when I got a few programs working for the first time by compiling. :)

---

### Post by y@w on 2008-11-14
The packages are made for distributions of Linux that are deemed 'popular enough' by the developer and then anyone who wants it on a different distribution can compile it themselves. It allows greater flexibility as far as choices in platforms. You can certainly get source for software for Windows and compile it yourself if you really want to, but Windows really only has 32-bit and 64-bit in each version.

---

### Post by go_beep_yourself on 2008-11-25
It's not possible to compile most software in Windows because the source is not available, non open source software. That's why it is possible to compile more software in Linux than Windows.

---

### Post by Paqman on 2008-11-25
One thing to watch out for when compiling is that it will break the dependency system in your package manager, so can make your system unstable.

You should only compile as an absolute last resort. To keep your system running stably you should stick to getting software from the repos or proper .deb files.

---

### Post by kpkeerthi on 2008-11-25
Be sure to compile and install using [checkinstall]("https://help.ubuntu.com/community/CheckInstall") so you can use your favorite package manager to uninstall it later.

As for your original query...
You can compile in linux because most of the applications in Linux are open source. Your distribution already provides precompiled binary packages (debs in Ubuntu). But some advanced users choose to compile from source because they might need latest version of the package may be because they need a feature that is not available in the binary package. Compile from source in Linux is an option, not a must.

You can also compile from source those apps that are open source, in Windows. But since most windows applications are proprietory and closed source, you normally install using vendor-provided installer or MSI.

---

### Post by go_beep_yourself on 2008-11-25
Sometimes the latest version of software isn't available as a deb. That's a reason to compile. And a few times, I wanted games in 64-bit that were only available as 32 bit, so I compiled them.

---

### Post by ByteJuggler on 2008-11-25
> **LinuxFox said:**
> 
I'm not complaining or trying to offend anyone, but it just has me wondering why some software is like this.

In addition to what others have said, part of it has to do with the philosphy behind free (as in freedom) software:  People who write free software believe that software is like knowledge and maths - you should be free to learn from it and improve on it, and be able to build/work on the work of others freely as in science.  As Isaac Newton said, "If I have seen a little further it is by standing on the shoulders of Giants."  

Giving someone the source code in principle gives them the the ultimate freedom to make use of software by looking at the guts of the program, allowing them to learn from it, improve it, build on it, move it to another platform, etc.  These are freedoms you do not have with proprietary or binary only software.  By the way, "free" (freedom) software does not neccesarily mean "gratis", many people are actually employed and paid good money for writing free open source software, others in a sense are recompensed non-monetarily by insisting that downstream changes made by others also being made free (so the original author may benefit/be recompensed through other's efforts through their improvements) through free software licenses like the GPL.  Still, many do write free software for the love and joy of the experience in a gratis fashion.

---

