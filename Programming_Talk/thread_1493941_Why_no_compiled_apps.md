---
title: "Why no compiled apps?"
date: 2010-05-26
forum: Programming Talk
---

### Post by palz2015 on 2010-05-26
Why is it with unix and unix-like (oh yeah, and linux) that people cannot just download, say, Firefox without:
A) compiling a source
B) using a package (deb, rpm) to install the source

I just dont get the whole source code junk :).

---

### Post by lavinog on 2010-05-26
> **palz2015 said:**
> Why is it with unix and unix-like (oh yeah, and linux) that people cannot just download, say, Firefox without:
A) compiling a source
B) using a package (deb, rpm) to install the source

I just dont get the whole source code junk :).

What is wrong with using the package manager to install firefox?

Usually a deb package is already compiled.  That is why you have to specify 32bit or 64bit.


The problem is architectures can vary.  You can compile something to be 64bit and distribute it, and only 64bit users can use it.
You can compile it as 32bit, and everyone could use it, but the 64bit users do not get the benefit (and could take a performance penalty too)

---

### Post by Seq on 2010-05-26
> **lavinog said:**
> What is wrong with using the package manager to install firefox?

Usually a deb package is already compiled.  That is why you have to specify 32bit or 64bit.


The problem is architectures can vary.  You can compile something to be 64bit and distribute it, and only 64bit users can use it.
You can compile it as 32bit, and everyone could use it, but the 64bit users do not get the benefit (and could take a performance penalty too)Plus 64-bit users would have to have duplicate copies of libraries in their 32-bit form. Also, this is only applicable to x86 machines. There is no binary compatability between ARM, x86, and PowerPC. So one build wouldn't work.

To answer the original question: Use ubuntu's software centre, tell it to install firefox. You don't have to mess around with packages or source, the system does it for you.

---

### Post by MadCow108 on 2010-05-26
a package (manager) is just a unified installer (and more). And as mentioned normal packages you usually install contain precompiled binaries and no source.

Technically there is no big difference in what happens when you double click a setup.exe or a package.deb
Just in windows every program does its own thing, resulting in a gigantic hard to maintain mess.

compiling source code is only necessary when there is no package available.
Its the same on windows when there is no setup file available (which is less often the case as compiling in windows is connected with more work than on typical unix systems).

---

### Post by palz2015 on 2010-05-30
I was just using firefox as an example;  I'm using it right now :popcorn:
And windows setup programs are just a program, a .cab or something containing what needs to be installed, precompiled. 

For instance, there is this program called qtparted. I downloaded the source. I am wondering why I cannot download a file called qtparted.bin or just qtparted (the executable), but I must install it via a package or compiling.

---

### Post by CptPicard on 2010-05-30
> **palz2015 said:**
> I downloaded the source.

...why?

> 
 I am wondering why I cannot download a file called qtparted.bin or just qtparted (the executable), but I must install it via a package or compiling.

Well, the package is, essentially, the ".cab" that contains everything that needs to be installed. It also knows of its dependencies to other packages, so the package manager is capable of configuring the system as needed.

---

### Post by PhilGil on 2010-05-30
A Windows installer is not all that different from a .deb package.  If anything, it's probably more complex.  Only the most rudimentary Windows programs consist of a single executable file.  A typical windows installer is a wrapper/installation script for the main program executable, associated programs, linked libraries, configuration files, menu items, registry entries, etc...

---

### Post by sgosnell on 2010-05-30
What people are trying to tell you is that Windows lies to you.  You get a .exe file, but it's not really a compiled executable file, it's a package containing lots of different types of files, and installing it involves extracting the contents, futzing with your registry, copying all sorts of .dll and configuration files to your HDD, etc.  A .deb file is pretty much the same, containing compiled binaries, perhaps some shared libraries, and various script and configuration files.  You can install the .deb file by double-clicking on it, just as you can install the Windows .exe file by double-clicking on it.  The results are the same, but you don't have the risk of having your registry modified in Ubuntu.  Things aren't seen by the user exactly the same in the two OSs, but the process is essentially the same.  The biggest difference is that in Ubuntu you can use the package manager, update manager, or software sources manager to install the packages automatically, without having to download the packages and supporting files separately.  Just tell Synaptic to install something, and it does it, without you having to do anything except enter your password.  

There are packages not in the repositories which you may have to get yourself, and there are some packages that aren't distributed as .deb files, but that's the choice of the developer, and has nothing to do with the OS itself.  Some developers just don't want to take the trouble to package their software into .deb files, and that's their choice, and you get what you (don't) pay for.  Some Windows software doesn't come in a setup/install package either.

---

### Post by OgreProgrammer on 2010-05-30
> **palz2015 said:**
> 
B) using a package (deb, rpm) to install the source

I just dont get the whole source code junk :).

And how is that any different than using an msi or exe installer in windows? Its not.

---

### Post by lavinog on 2010-05-30
> **palz2015 said:**
> For instance, there is this program called qtparted. I downloaded the source. I am wondering why I cannot download a file called qtparted.bin or just qtparted (the executable), but I must install it via a package or compiling.
I am pretty sure the qtparted project is dead since the 0.4.5 version is dated 2005.

```

ChangeLog for QtParted:
-----------------------

* 0.4.5 (2005-08-12)
  - Fix up "&" signs being displayed in the menus w/ Qt 3.3.4
  - Add workaround for parted bug showing CD-ROMs as partitioning targets
  - Some code cleanups
  - Some bugfixes

```

Would it even support ext4?

You shouldn't need to compile anything unless you really want to.  If you find yourself in a position where you need to compile something, you might be able to file a bug report to request the application to be added to the ubuntu repositories.

The great thing about using a package manager over a single installer is that all of your packages can be kept up to date.

---

### Post by diesch on 2010-05-31
> **palz2015 said:**
> Why is it with unix and unix-like (oh yeah, and linux) that people cannot just download, say, Firefox without:
A) compiling a source
B) using a package (deb, rpm) to install the source


You can do that if the software vendor has made some kind of installer package for your platform - some do.

But using your distribution's package format (like .deb or .rpm) to install software is usually much easier

> **palz2015 said:**
> 
I just dont get the whole source code junk :).

Most software for unix-like platforms runs on a lot of different, often binary-incompatible platforms. To make binaries available for all this platforms is expensive (often you need different hardware) and time consuming. 

By distributing the source code the programmer saves his time and money and the user is often able to use  the software on platforms the programmer doesn't have access to. He even can modify the source code to adapt it to his needs or to remove bugs - all without waiting for the original programmer. That's cool.

As all this compiling stuff is a bit to much for most users people started to put together collections of precompiled software with everything you need to run it - that's called a distribution.

---

### Post by palz2015 on 2010-05-31
Let me back up a bit. I just want to know, packages aside, why, especially for older programs, I have to download a source.tar.gz and make that myself. A good number of windows programs are standalone executables. Why can't I download a unix executable and just run it as I would a windows program.exe?

---

### Post by slavik on 2010-05-31
> **palz2015 said:**
> Let me back up a bit. I just want to know, packages aside, why, especially for older programs, I have to download a source.tar.gz and make that myself. A good number of windows programs are standalone executables. Why can't I download a unix executable and just run it as I would a windows program.exe?
1. because libc version changes
2. because creating a proper package is not simple
3. because the developer doesn't have time nor care to create a compiled package
4. are you complaining?

---

### Post by lavinog on 2010-05-31
> **palz2015 said:**
> A good number of windows programs are standalone executables.
And a good number of windows programs do not install properly in the recent versions of windows.

Are you trying to use qtparted instead of gparted?

---

### Post by Milliways on 2010-05-31
> **palz2015 said:**
> For instance, there is this program called qtparted. I downloaded the source. I am wondering why I cannot download a file called qtparted.bin or just qtparted (the executable), but I must install it via a package or compiling.

A simple google search would actually find a .deb for qtparted, but the wikipedia entry tells you it is discontinued.

Why not use gparted, or better still Disk Manager, which replaced it in Lucid.

---

### Post by Milliways on 2010-05-31
> **palz2015 said:**
> Let me back up a bit. I just want to know, packages aside, why, especially for older programs, I have to download a source.tar.gz and make that myself. A good number of windows programs are standalone executables. Why can't I download a unix executable and just run it as I would a windows program.exe?

There are very few Windows programs which you can download and just run.
They are generally simple programs.
Most more complex programs contain many files, and the exe is really an installer.
It is done this way because most Windows users couldn't install a msi 

There are quite a few Windows programs distributed as source, but these are no use to most Windows users, as Windows does not come with a compiler.

In fact you can download Linux executables; I have distributed code this way myself.
This is not particularly efficient, as it requires the user to satisfy dependencies, or the use of a statically linked program, and even then will only run on specific platforms.

Incidentally you could write a Linux executable which installed a program, but when you have simple installers would you want to?

Incidentally Mac also uses packages.

If you want an OS that works like Windows, then stick to Windows, otherwise learn to adapt to different ways of doing things.

---

### Post by Can+~ on 2010-05-31
> A good number of windows programs are standalone executables. Why can't I download a unix executable and just run it as I would a windows program.exe?

Because you're dealing with different philosophies. Windows philosophy, is handing you everything, even if you already have it, they usually link against the most basic API windows offers, everything that is "guaranteed" to be there, and then pack what's missing.

On the other hand, you have debian, which has a repository and package system, which solves the dependancy tree, where most of the libraries are there, and therefore, if you want to install something new, you just give the essential code, and the libraries are specified in the installing containing pack (deb, rpm, w/e). Debs are pre-compiled (or compiled upon install) and linked to the local libraries.

So it all boils down to the fact that Windows has no centralized library handling mechanism, they just dump .dlls wherever they feel like it. So, mostly, it's not a feature, but a side-effect.

---

### Post by palz2015 on 2010-06-14
> **Milliways said:**
> A simple google search would actually find a .deb for qtparted, but the wikipedia entry tells you it is discontinued.

Why not use gparted, or better still Disk Manager, which replaced it in Lucid.
Honestly, gparted is the best. I was just using it as an EXAMPLE.

---

### Post by amauk on 2010-06-14
as others have said,
Binary packages (as found in most linux repositories) are compiled

they are packages that contain any of the following:
- Binary executables - placed in one of the "bin" directories
- shared libraries - placed in one of the "lib" directories
- Configuration files - placed in /etc and/or user's home directory
- shared resources (eg. icons, etc.) that get placed in one of the "shared" directories

They are no different (big picture view) from windows installer exe files, or MSI files

They are a collection of files, compressed into a single file that can be "installed"

Bear in mind that Windows targets (by and large) only two architectures - x86 and x86_64
Linux on the other hand caters for many (many) more architectures

Also bear in mind that there are differences between all the different Linux distros, and often a compiled package for one distro will not install on another
(as said already, different version of core libraries / utilities, and differences in filesystem layout and distro conventions)

Upstream software authors (particularly small or niche audience apps) tend to release source only as they do not have the time or resources to build and host compiled versions of their software to cater for different distros or different architectures
instead relying on the distro maintainers to package their software

---

### Post by palz2015 on 2010-06-14
So, the reason you tend to find source code is the difference in distros, and when compiled it is "made" for that distro? And packages just make the installation simpler?

---

### Post by amauk on 2010-06-14
Yes
It's division of duty and resources

The author of the software writes the software.
That's what he does

He doesn't care if you use Ubuntu on x86, or Fedora on PowerPC, or Debian on Arm

He writes (and distributes the source to) his software

The various distros come along, package his software, and include in in their respective repositories

---

