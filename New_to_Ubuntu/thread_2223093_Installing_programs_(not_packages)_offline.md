---
title: "Installing programs (not packages) offline"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by peysun1 on 2014-05-09
Hi,


In windows, you can install a program off-line by copying "somefile.exe" on a usb, transferring the file to an off-line PC, and executing "somefile.exe" there.


In ubuntu, I understood that things are a bit more complicated. To install a program on your off-line PC, you should somehow find out what "packages" are associated with your program (true?). Once you know the required packages, then there are many ways to install them on an off-line PC (for instance using Synaptic, etc).


For a newbie, finding the associated packages and package dependencies could be a difficult task. Is there a simple way to install programs (not packages) on an off-line PC? (I am talking about something equivalent to software centre, where you choose your PROGRAM, and it takes care of all the required packages and dependencies. Then you copy its output on a usb and install it on an off-line PC).


Thanks

---

### Post by tfrue on 2014-05-10
It's similiar, in a way, to Window's as I could download "somefile.deb" (.deb for Ubuntu since .exe is for Windows) and move the file to a usb and then transfer that file to an offline PC and execute "somefile.deb" to install the software. But you would need an on-line PC just to download the file, and then you would be ok since the somefile.deb would install the libraries and dependencies without internet. 

> In ubuntu, I understood that things are a bit more complicated. To  install a program on your off-line PC, you should somehow find out what  "packages" are associated with your program (true?). Once you know the  required packages, then there are many ways to install them on an  off-line PC (for instance using Synaptic, etc).

To clear your confusion, in Ubuntu, or Linux really, you download a programs source code, which is basically the program, and compile the source code, using a compiler, to install the program to a usable state on your PC; Depending on the libraries and other dependencies on your computer, you may have to compile and install newer libraries or other dependencies for the program to operate. The way you say "packages" is a bit misleading, instead of packages use dependencies as the software needs dependencies, like libraries, to operate properly and there are many ways to find out what dependencies your desired software needs, for instance "packages.ubuntu.com" or trying to compile the code and the compiler telling you what you need. When you say "Once you know" it's more of once you download the dependencies and compile them on the offline PC but you wouldn't use Synaptic as that is a package manager, which can be used to find information or download a specific library, you would use the GCC compiler in Ubuntu or a different installed compiler.

If you have Ubuntu 14.04, then you will have what you need to compile code, but you should install *build-essentials* just to make sure that you have the essentials for compiling. Let's say that you want to install Wireshark so you download the source code and begin compiling it, but the compiler says that you need other dependencies first for you to install this program, like gtk+. So you download gtk+ and begin to compile it so you can install Wireshark, but gtk+ says that you need to install glib and cairo and blah blah blah. You begin to see why it becomes frustrating and time consuming.

The main process of installing from source is to download the source file, extract it, run "./configure" "make" and "make install" in the newly extracted directory, which will tell you if your computer is ready and all the libraries and dependencies are good, then install it to your system. There is a bit more interaction from the user, but that is essentially what you will do.

Here are some links that I found extremely useful and would explain things in a much more concise way that I can:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) (This explains a lot very well)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) (The quick start guide to compiling)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) (For a more in-depth look at compiling)

Hope this helps,
Chris

---

### Post by philinux on 2014-05-10
> **peysun1 said:**
> Hi,

For a newbie, finding the associated packages and package dependencies could be a difficult task. Is there a simple way to install programs (not packages) on an off-line PC? (I am talking about something equivalent to software centre, where you choose your PROGRAM, and it takes care of all the required packages and dependencies. Then you copy its output on a usb and install it on an off-line PC).


Thanks

There is aptoncd [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Have a read it may be what you want.

---

### Post by stalkingwolf on 2014-05-10
if you have the programs installed on one computer and want to put them on another. aptoncd might be the ticket.  I also see apt-offline although i have never used it.

---

### Post by peysun1 on 2014-05-13
I'll be offline :) for about a week, and can't try your suggestions yet. Thank you guys for your help!

---

### Post by buzzingrobot on 2014-05-13
> **peysun1 said:**
> I'll be offline :) for about a week, and can't try your suggestions yet. Thank you guys for your help!

You only need to know the name of the package that contains the program you want to install.  You do not need to know the names of any other dependencies that package requires. Any dependencies are identified, downloaded and installed by the Software Center (or any other similar application that does the same thing, e.g. Syanptic, apt-get, etc.)

Obviously, if you are not online, those packages cannot be downloaded. There are ways to determine the dependencies for a given package.  All those files could be downloaded and installed later, offline.

The same general principle applies in Windows.  If the file you are trying to install requires additional files, then those files needed to be downoaded and installed. Because Windows inherits from the DOS tradition that saw applications distributed with all their required files in one compressed archive, and because DOS did not really enforce any guidelines about what files went where, Windows applications are still often packed into a single compressed archive that can be expanded into one directory and executed. This often results in having many support libraries needed by various applications duplicated across the filesystem. Linux takes a different approach, using shared libraries located in standard locations that only need to be installed once and are then available to all applications. Attempts to emulate the Windows approach should be avoided.

It is simply not true that Linux users need to compile their own programs from source code. Ubuntu and other Linux distributions maintain repositories with tens of thousands of easily installed programs.  Someone lacking sufficient knowledge of Linux software development and the packaging and dependency resoultion strategy used on his/her system can do considerable harm to that system by copying and pasting compilation instructions from some random internet site.

---

