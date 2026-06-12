---
title: "how stand alone applications work"
date: 2013-05-06
forum: Programming Talk
---

### Post by IAMTubby on 2013-05-06
Hello,
I was just wondering how "stand alone applications" work. I mean, many a times, it happens that you get an executable and you don't have to install it, just double clicking it starts the application. But don't they have to "install", as in, copy required object files/libraries to specific system locations etc.

An example of this situation was when I was using 1.putty and 2.eclipse on windows.
I never installed these, nor did they ask me for some license agreement etc. Just double clicking them worked.

Though I no longer use windows, I would like to understand how they worked.

Thanks. 

PS : As an aside, is my understanding of "installation"(from above) correct ?

---

### Post by lisati on 2013-05-06
A simple program which a relatively uncomplicated purpose, such as displaying "Hello world" on your screen, can usually be compiled as a stand alone program. It can be placed in just about any location you choose on your hard drive without being tied to a specific location. There's less of a need to break it up into parts that can potentially be scattered in various locations than might be the case with a larger, more complex programming tasks.

---

### Post by ofnuts on 2013-05-06
The "installation" does several things:

1) determine the right place to put the various files, and unpack them there
2) create a startup icon
3) make the program known to the rest of the system (for instance, associating it with some file types)
4) do whatever is necessary to make de-installation easy

Most of this can be done manually, but you'd have to read the doc...

---

### Post by slickymaster on 2013-05-06
The basic definition of a standalone application is a program that functions as is, when booted up or launched.
Another meaning of standalone software refers to the location from which it runs. There is some software that can run from a storage device without actually being installed on the computer. Software that does not require installation, but can still be run is another meaning given to the term standalone software.
Some programs cannot run without calling upon resources from the system, for example. A piece of software that runs without reference to the environment is another type of software that is referred to as a standalone program.

---

### Post by shawnhcorey on 2013-05-06
Stand-alone applications work because they have everything they need inside themselves. Applications often use external libraries full of useful software. Libraries can come in two versions, shared (*.dll on Windows, *.so on Linux) and not shared. Stand-alone apps are compiled with the not-shared libraries and need nothing but themselves to run.

---

### Post by pbrane on 2013-05-06
As shawnhcorey pointed out these types of applications or programs have all required libraries statically linked during the build. Otherwise the program would have dependencies that the OS would have to satisfy. On windows that may not be too hard, but there are many different flavors of GNU/Linux distros.

---

### Post by shawnhcorey on 2013-05-06
> **pbrane said:**
> As shawnhcorey pointed out these types of applications or programs have all required libraries statically linked during the build. Otherwise the program would have dependencies that the OS would have to satisfy. On windows that may not be too hard, but there are many different flavors of GNU/Linux distros.

That was called [Dependency Hell]("http://en.wikipedia.org/wiki/Dependency_hell") and has been solved. Actually, finding all the dependencies on Windows is harder especially if they're third party, not Microsoft, ones.

---

### Post by IAMTubby on 2013-05-11
shawnhcorey, pbrane, slickymaster, ofnuts
Thanks a lot for all the answers,it is now clear :)

---

### Post by nvteighen on 2013-05-11
Just be aware of something. Only the OS is completely stand-alone (except that it requires a bootloader to boot up, but that's somehow in another league, I think). Even if you wrote a program with all its libraries statically linked in it, you still would require the kernel to be able to execute the executable format the binary is in, e.g. usually ELF in Linux. Try running any Windows executable in Linux (without using Wine); it will fail  because the kernel doesn't know how to understand those binaries at all.

---

