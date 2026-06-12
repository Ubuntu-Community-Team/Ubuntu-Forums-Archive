---
title: "Compiling packages on/for OSes with no gcc or make"
date: 2010-10-28
forum: Packaging and Compiling Programs
---

### Post by terminator14 on 2010-10-28
If you have a tar.gz source package, how can you compile it to work on a linux system that has no gcc or make and no package manager to get either? 

Example:

I've ran into things like ipfire or astaro, which are basically distributions made from scratch ([lfs]("http://www.linuxfromscratch.org/") style). Neither have gcc, make, or a package manager with the packages I want. Can I compile a tar.gz on a different machine with gcc and just scp it over? (The following questions assume I can)

The problem with this is that the cpu architecture of the machine that will be compiling and the one the distribution runs on may be different. There must be a way to tell make to compile the package for a different architecture, isn't there? Or is it absolutely essential that the architectures be exactly the same?

The second problem seems to be the kernel. Often it looks like you need the kernel headers for the OS you are trying to compile for in order for everything to go smoothly. Why are the kernel headers needed? Are they only needed if what you're compiling creates a kernel module? Is it enough to just copy the folder with the kernel headers from the OS you want to compile for and point make towards the folder? If this will work, how can you tell make (or ./configure) where to look for those headers?

Some software also asks for you to be running the kernel that the software will need to run on. How can I compile on one version of a linux kernel with certain options chosen when the kernel was being compiled, and run the software on a completely different version of the kernel where completely different options were chosen when the kernel was compiled? Is this what the kernel headers address?

What about installing? In this case, since you can't run "make install" on the OS you are compiling for (since it has no make), is there an easier way to copy the binaries from the folder where you compiled them to the OS where you need them than one by one? Is there a list created of what binaries were made, and where they should go (perhaps the one that make install uses)?

Also, there may be a problem with libraries that were there during the compile process, but are not there in the OS that will run the binaries. One solution would probably be just to run the binary and see what libraries it complains about missing and copy those libraries by hand. Is there a way however to tell make to include the libraries in the binary when it is compiling the program so that the binary is self-contained?

Some of my questions may sound dumb as I have limited knowledge of programming, but if someone can straighten me out, I'd be grateful.

---

