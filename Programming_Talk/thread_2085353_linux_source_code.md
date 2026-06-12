---
title: "linux source code"
date: 2012-11-17
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-17
Hey,
I recently bought a book which gives a brief explanation of underlying implementation of the various algorithms unix uses.
I love it, but I would like to read the book along with the actual source code, so that I can learn a few things better and relate.

Where do I get the actual source code ?
Is it the linux kernel source from kernel.org ? 

But, the reason I'm confused is, I know gcc and a whole lot of things come with binutils. So, do I have to download multiple .tar.gz's ? Can't I get one single file which contains all the source code ?(that is, all the algorithms + binutils + ... == everything that linux uses)

Thanks.
Please advise.

---

### Post by Bachstelze on 2012-11-17
> **IAMTubby said:**
> Hey,
I recently bought a book which gives a brief explanation of underlying implementation of the various algorithms unix uses.
I love it, but I would like to read the book along with the actual source code, so that I can learn a few things better and relate.

Where do I get the actual source code ?
Is it the linux kernel source from kernel.org ? 

The actual source code of what? Chances are that your book is not based on any actual code, but discusses algorithms at a higher level. It is possible that Linux uses those same algorithms, but you will have to look for them.

> But, the reason I'm confused is, I know gcc and a whole lot of things come with binutils.

What do you mean by "binutils"? The only binutils I know are the GNU binutils, which are a set of, well, utilities to work on binary files (like objdump or ar). It has nothing to do with the algorithms used in an operating system kernel.

---

### Post by Lars Noodén on 2012-11-18
The source code for the linux kernel is available at kernel.org : [http://kernel.org/](http://kernel.org/)

However, that is the unmodified kernel.  What is used in the various distros, including Ubuntu, is usually quite modified.  You can get the source that is actually used through apt-get.

```

cd /usr/src
apt-get source linux-image-3.5.0-17-generic

```

---

### Post by 681ankit on 2012-11-18
If you want linux 0.01 kernel (the first version easy to read and get)source-code then here's a link ..And newer versions of linux kernel are available at given site kernel.org..

[http://dl.dropbox.com/u/85906715/linux%200.01.rar](http://dl.dropbox.com/u/85906715/linux%200.01.rar)

---

### Post by IAMTubby on 2012-11-21
> **681ankit said:**
> If you want linux 0.01 kernel 
That was a really good suggestion :)
I downloaded it, haven't gone through it completely. Thanks.

> **Lars Noodén said:**
> The source code for the linux kernel is available at kernel.org : [http://kernel.org/](http://kernel.org/)

Thanks Lars

> **Bachstelze said:**
>  It(edit by IAMTubby: "it" refers to   binutils) has nothing to do with the algorithms used in an operating system kernel.
I was wanting to know if it's possible to download every source that is part of the operating system, which includes kernel, binutils etc. I actually do not know what's the package I'm looking for myself. Am I looking for, the source code of ubuntu, maybe ?

---

### Post by JKyleOKC on 2012-11-21
> **IAMTubby said:**
> I was wanting to know if it's possible to download every source that is part of the operating system, which includes kernel, binutils etc. I actually do not know what's the package I'm looking for myself. Am I looking for, the source code of ubuntu, maybe ?There are more than 30,000 separate packages, I've been told, that **could** be part of the operating system. Do you really want to download and pore through the millions of lines of source code for all of them?

Some years ago, as part of my research that led to publication of "Undocumented DOS," I actually did a complete disassembly of MS-DOS 4.0, taking it back down to machine-code level. That was less code than a Linux kernel, but it took several months of full-time effort to understand what it was doing -- and I already understood most of the algorithms involved.

Later, doing research for another book that never saw the light of day, I downloaded the source code for the "ftape" portion of the Linux kernel. That's the part that handles the actual reading and writing of QIC-80 magnetic tape cartridges, which were the standard backup medium before large hard drives became affordable. Despite several months of analysis, and hints from folk more expert than myself, I never did comprehend all of the details about it before the project sputtered to a halt due to the rapid advance of hardware development.

The communication problem involved here is simply that "the operating system" isn't a single clearly defined concept. To some folk, it's only the group of core programs that enable booting up the machine, selecting programs to run, and handling input and output for those programs. To others, it's the whole computer-as-appliance package, including all the utility programs, development tools, and applications.

Learning about that first definition is daunting but possible, and can be a really fun ride while doing so. Learning all about the second is almost impossible, since the package changes faster than humans can learn about it.

---

### Post by pbrane on 2012-11-21
Perhaps you're looking for the GNU operating system source?
 [http://www.gnu.org/]("http://www.gnu.org/")

The Linux kernel is not actually the operating system, it's the part the OS runs on. 
If you want to understand more how a complete GNU/Linux system is built you should have a look at Linux From Scratch, 
[http://www.linuxfromscratch.org/lfs/]("http://www.linuxfromscratch.org/lfs/")

---

### Post by Bachstelze on 2012-11-21
> **IAMTubby said:**
> 
I was wanting to know if it's possible to download every source that is part of the operating system, which includes kernel, binutils etc. I actually do not know what's the package I'm looking for myself. Am I looking for, the source code of ubuntu, maybe ?

You can download the source code from which any Ubuntu package was compiled. To get the source code for a given package, if you are on an Ubuntu system you can do

```
apt-get source PACKAGE_NAME
```

Otherwise you can get it from [http://packages.ubuntu.com](http://packages.ubuntu.com)

The same idea applies to other distros but the method to get the source code will vary (especially on non-Debian-based ones). Or, of course, you can download a source tarball of a program directly form the developers, but it's a bit more time-consuming...

---

### Post by IAMTubby on 2012-12-01
Sorry for the late reply, I was out of station and didn't have access to a system.

> **JKyleOKC said:**
> 
Learning about that first definition is daunting but possible, and can  be a really fun ride while doing so. Learning all about the second is  almost impossible, since the package changes faster than humans can  learn about it.
Thanks for sharing your experience JKyleOKC.

> **pbrane said:**
> you should have a look at Linux From Scratch, 
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)
Thanks pbrane, the link was really useful

> **Bachstelze said:**
> 
```
apt-get source PACKAGE_NAME
```Otherwise you can get it from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Thanks Bachstelze, was very useful as always.

---

