---
title: "What does windows OS use??"
date: 2009-02-01
forum: Other OS Talk
---

### Post by myromance123 on 2009-02-01
Okeh Im quite the beginner at OS infrastracture, but my curiosity is killing me.

 From what I understand a kernel is like the basic brain of a Unix system no?

 So what is MS-DOS to windows? is it like a kernel?
  Or are these to things completely different?

As well, why is Windows not listed as a Unix OS?
  There are times I see in books that BSD is also not Unix but then there are times its listed under Unix too?

 What is it that separates these OSs from one another?

If you know the answer(s) or know a wiki/website/book which helps understand or answers these questions then please do share :D

---

### Post by orethrius on 2009-02-01
Ohhhh boy, this is something of a complicated issue, but I'll explain as best as I can.
It's something of a twisted tale of intrigue and double-crossing, but there is much to be learned here.

Windows is to Gnome/KDE/XFCE/Busybox/whatever, as MS-DOS is to the command-line shell (BASH or what have you), as the NT kernel is to the Unix kernel.

Now I mentioned that this is somewhat complicated, and here's how.

Windows (anything newer than 3.11, at any rate) uses a "monolithic" kernel that attempts to include every possible function by default.
Linux and BSD use "modular" kernels that can be made to include new functions as necessary; these often show up in popular distributions as "monolithic" designs that attempt to include as many popular functions as possible.
Minix and QNX use a "micro" kernel that only attempts to handle core system functionality, with all usable features being handled as far away (design-wise) from the core system as possible.

Windows is simply not listed as a Unix OS because it doesn't use a Unix kernel.  BSD can be listed as either, depending on whether GNU (GNU's Not Unix) tools are included in the distribution.

Linux is unique in that it can implement Unix utilities without having a single line of proprietary source in its kernel; in fact, SCO attempted to prove otherwise, and essentially lost the court case when their position boiled down to six lines in a timer function that really can't be handled in a more efficient, less trivial manner.  They're still appealing the decision, though it's been found that Novell actually owns the right to pursue Unix copyright violations.  If anything, Andrew Tanenbaum would have more legal cause to go after Linus Torvalds - as he authored the original Minix microkernel that Linus used as his inspiration - but he's expressed no such interest, and the two continue to have debates about monolithic versus micro kernel designs to this day.  A good portion of the issues that Linux faces on the desktop today essentially trace back to a time when Microsoft acted to ban "bare" systems (shipped without an OS) with anti-piracy FUD, after which they somewhat successfully convinced hardware vendors to code exclusively for Windows APIs.

I hope this answers your question, but let me know if you need anything clarified (or if I got something wrong, guys, jump in)!

---

### Post by mips on 2009-02-01
A kernel is essentially the core/brain of an OS if you want to call it that.

MS-DOS used to be an OS with a monolithic kernel up until around 2000.
Earlier versions of windows up to 3.11 was basically just a GUI running on top of DOS.
With windows 95/98/ME DOS was incorporated into the OS for bootstrapping.
From Windows NT onwards DOS was no longer part of the OS.
95-Vista still however have a console that looks and behaves like dos although it's not really dos from NT onwards.

Windows is not a unix based on the design & operation of the OS, it's also not posix compliant.

BSD cannot be called "Unix" because they are not certified as such by the Open Group which owns the trademark. Certification is expensive and you have to certify every version number. There are certain requirements you have to meet which I don't know if BSD does and you won't really know until they try and certify it. As far as I'm concerned bsd is a unix.

Just search for the relevant terms on wikipedia, MS-Dos, Windows, Unix, Posix, BSD, Kernel.

---

### Post by jrusso2 on 2009-02-01
> **mips said:**
> A kernel is essentially the core/brain of an OS if you want to call it that.

MS-DOS used to be an OS with a monolithic kernel up until around 2000.
Earlier versions of windows up to 3.11 was basically just a GUI running on top of DOS.
With windows 95/98/ME DOS was incorporated into the OS for bootstrapping.
From Windows NT onwards DOS was no longer part of the OS.
95-Vista still however have a console that looks and behaves like dos although it's not really dos from NT onwards.

Windows is not a unix based on the design & operation of the OS, it's also not posix compliant.

BSD cannot be called "Unix" because they are not certified as such by the Open Group which owns the trademark. Certification is expensive and you have to certify every version number. There are certain requirements you have to meet which I don't know if BSD does and you won't really know until they try and certify it. As far as I'm concerned bsd is a unix.

Just search for the relevant terms on wikipedia, MS-Dos, Windows, Unix, Posix, BSD, Kernel.

Nice someone got it right I don't have to do it now.

---

### Post by RiceMonster on 2009-02-01
kernel is the "brain" of any operating system. Windows uses the NT Kernel. Windows still shares some similarities with MS-DOS, but it's not based off it anymore (Windows 9x is built ontop in DOS).

Windows isn't listed as a UNIX OS because it's not based off it and shares absolutely nothing in common with it. It's completely different.

Read about UNIX on wikipedia.

---

### Post by orethrius on 2009-02-01
> **mips said:**
> A kernel is essentially the core/brain of an OS if you want to call it that.

MS-DOS used to be an OS with a monolithic kernel up until around 2000.
Earlier versions of windows up to 3.11 was basically just a GUI running on top of DOS.
With windows 95/98/ME DOS was incorporated into the OS for bootstrapping.
From Windows NT onwards DOS was no longer part of the OS.
95-Vista still however have a console that looks and behaves like dos although it's not really dos from NT onwards.

Windows is not a unix based on the design & operation of the OS, it's also not posix compliant.

BSD cannot be called "Unix" because they are not certified as such by the Open Group which owns the trademark. Certification is expensive and you have to certify every version number. There are certain requirements you have to meet which I don't know if BSD does and you won't really know until they try and certify it. As far as I'm concerned bsd is a unix.

Just search for the relevant terms on wikipedia, MS-Dos, Windows, Unix, Posix, BSD, Kernel.

Thank you, mips.   Still, considering that ntoskrnl.dll is protected by NDAs that give corporate lawyers nightmares for weeks, one is left to wonder how much of that kernel is "new and innovative" and how much is "rehashed DOS GUI implementations". ;)

---

### Post by Sorivenul on 2009-02-01
mips has covered all the bases and basics.

In regard to BSD and other "UNIX-like" operating systems, I believe [this page]("http://www.netbsd.org/about/call-it-a-duck.html") from NetBSD says it best.

---

### Post by myromance123 on 2009-02-01
Ahh ,I see. I was wondering whether windows actually used a kernel and if so what it was named.

  Awesome now I can search better.
Let me just recheck that I understand correctly (and sorry if its in sort of a dumbed down version, I'm still quite the beginner)

So the kernel is practically the "brain" of an OS and every OS has one, no?

Windows used to run on DOS but now its completely NT Kernel based.
 BSD is not classified as Unix because they aren't certified.

May I ask another thing?
  Is every OS classified as Unix mean they have the same type of kernel?
Or at least a major part of the kernel for all Unix type OSs is similar?

Major thanks to all repliers especially orethrius and mips :D

 I give you the :KS medal for you service xD

---

### Post by myromance123 on 2009-02-01
Sorivenul,

  That page is hilarious xD
I was expecting a read-100-times-to-understand explanation of the matter, and all it uses is a  DUCK!

 Very Cool~

---

### Post by fistfullofroses on 2009-02-01
Operating systems all have kernels. Think of an OS as being built of layers. In the middle of this layered model, you have hardware. Surrounding the hardware you have the kernel, surrounding that you have a hardware abstraction layer, surrounding that you have either a command line interpreter or a GUI depending upon the OS. To be UNIX-like you need to conform to POSIX standards. Microsoft has come close with certain endeavors, but has consistantly chosen to do otherwise.

MINIX3, Fiwix, UNIX, BSD, Linux, Solaris, AIX, HP-UX, Linux-libre, RISCOS, GNU, OS X, Next, IRIX, Ultrix, Tru64, and Xenix are all consider Unix-like systems.

DOS, CP/M, Windows, OS/2, SkyOS, Solar_OS, Menuet, Syllable, BeOS, Visopsys, z/OS, Netware, and MacOS (pre 10) these are all non-Unix systems.

Micro-kernel vs Monolithic kernel design has no little to no bearing on whether or not a system is Unix like. MINIX3 is a microkernel, while Xenix is a monolithic kernel. Windows XP is a monolithic kernel while Windows 7 is a microkernel.

---

### Post by gjoellee on 2009-02-01
Windows has used the Windows NT kernel since Windows NT was released.

---

### Post by Mason Whitaker on 2009-02-01
**The Structure of a Computer**
User 
Software
Operating System
Kernel
Hardware

The user is someone who determines what he wants the computer to do. Remember, computers are incredibly fast but incredibly stupid, and require humans to tell them what to do. Software is the common ground between the user and the computer. Software allows normal humans to command a computer with functions, but the functions were predetermined by a programmer, someone who had originally told the computer what to do. The operating system is the middle ground between the user and the kernel, and brings computing down the human level to where we can act and comprehend ( we don't exactly read 0's and 1's as efficiently as computers do ). The kernel can be described as the central brain of the computer where all data is managed, only demi-gods can actually comprehend what really goes on in the kernel. Finally, we have hardware, which is the physical part of the computer. All your graphics cards, hard drives, and monitors are hardware.

Hope this helped any :X

---

### Post by Foster Grant on 2009-02-02
> **myromance123 said:**
>  So what is MS-DOS to windows? is it like a kernel?

MS-DOS is dead. [http://en.wikipedia.org/wiki/MS-DOS#End_of_MS-DOS](http://en.wikipedia.org/wiki/MS-DOS#End_of_MS-DOS)

> As well, why is Windows not listed as a Unix OS?

Windows is not a POSIX-compliant OS. Therefore it's not Unix or a variant. [http://en.wikipedia.org/wiki/Posix](http://en.wikipedia.org/wiki/Posix)

---

### Post by albinootje on 2009-02-02
> **myromance123 said:**
> From what I understand a kernel is like the basic brain of a Unix system no?
> 
Normally every OS has a kernel, which is just one file.

 So what is MS-DOS to windows? is it like a kernel?

In MS-DOS there were the files msdos.sys and io.sys in C:, one of them was the kernel afaik.
I don't know what the kernel name is in the MS Windows versions.
> 
As well, why is Windows not listed as a Unix OS?

For being called Unix or Unix alike, you would have to follow certain POSIX standards.
I think I've read that only Windows NT partially followed that.
> 
  There are times I see in books that BSD is also not Unix but then there are times its listed under Unix too?

Unix is a trademark. 
Linux and FreeBSD, NetBSD, OpenBSD are Unix alikes, or Unix derivates.

See here for more background information :
[http://en.wikipedia.org/wiki/Unix](http://en.wikipedia.org/wiki/Unix)
[http://en.wikipedia.org/wiki/BSD](http://en.wikipedia.org/wiki/BSD)

---

### Post by ezsit on 2009-02-02
> So what is MS-DOS to windows? is it like a kernel?
Or are these to things completely different?

As well, why is Windows not listed as a Unix OS?
There are times I see in books that BSD is also not Unix but then there are times its listed under Unix too?

What is it that separates these OSs from one another?

MS-DOS and the current Windows Vista are very different beasts. MS-DOS was a single-tasking, 16-bit, command line operating system that consisted of a kernel and command line interpreter with a lot of additional yet separate programs to make up an operating system. 

Windows Vista is the descendant of Windows NT 3.1. Windows NT was originally designed as a microkernel operating system by David Cutler (MS got him from DEC). Windows NT 3.1 through 3.51 was a unique microkernel design that was portable (ran on x86, MIPS, Alpha, & PowerPC CPU's, both 32 and 64 bit), contained a POSIX compatible layer, an OS/2 compatible layer, and a DOS compatible layer. These compatibility layers were rudimentary and limited, but MS was making an attempt to be cross compatible. Starting with NT 4, the microkernel grew into a monolithic-style kernel by running the graphics subsystem and filesystem code within the memory space of the kernel. 

Here is one definition of micro vs. monolithic kernels - microkernels typically run as little code as possible inside the kernel context and memory space. Things like device drivers, filesystem code, GUI's, network stacks are all running outside of kernel space in a microkernel design. Very few OS's are tru microkernels, QNX is one. Almost all Unixes are NOT microkernel designs. Linux, BSD, Solaris, AIX, etc, are not microkernel designs. OS/X from Apple is one example of a Unix type operating system that uses a microkernel, borrowed from MACH and the research done at MIT back in the 1980's that NeXT used for the NeXT Step operating system.

Monolithic kernels, like Windows Vista, Linux, BSDs, Solaris, all run a ton of code withing the kernel address space and context. Windows and most Unixes run the filesystem code, the network stack, and device drivers all within the kernel address space and context. Windows goes one further and runs the GUI in the kernel space too. Monolithic kernels perform better than microkernels, at least with regards to user experience.

Unix is a trademark and tightly controlled. The process and expense of having an operating system "certified" as Unix is not worth BSD's time and effort, plus everyone knows the BSD's are unix, not Unix. Windows is a proprietary kernel that bears no resemblance to Unix, however, Windows does maintain some POSIX compatibility which gives it some unix-like features.

As for the separation of OSes? Many things differentiate OS designs and implementations. Do a Yahoo search on operating systems and you will be amazed at the number and variety. Windows, Unix, OS/X, Linux are just four. There are hundreds of operating systems, mostly research projects (as opposed to commercial) but there a many niche commercial operating systems out there. Just think of the system running ballistic missiles, now there's an operating system that I wouldn't know a thing about. :-)

---

### Post by Grant A. on 2009-02-02
I would just like to add that Linux has never been, nor ever will be "UNIX-based", Linux is simply an original kernel inspired by the UNIX kernel. They share no code what-so-ever.

The *BSDs are UNIX, but are not the true UNIXs. BSD broke off in the UNIX source tree way before UNIX System Revision IV (Or I for that matter), ever came out. 

Here is a nice little diagram of the origins:

[http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg]("http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg")

(It's an SVG, so it's resizable. If it doesn't work correctly, hit "CTRL -" a couple times.)

---

### Post by cardinals_fan on 2009-02-02
> **albinootje said:**
> 
Unix is a trademark. 
Linux and FreeBSD, NetBSD, OpenBSD are Unix alikes, or Unix derivates.

The BSDs are direct descendants of Unix.  Linux is not.

---

### Post by alex.rayu on 2009-02-03
Listing Operating System and Kernel as components of computer is incorrect. Kernel is included in the OS. Kernel is the basic group of functions that provide the basic activity of the operating system.

---

### Post by handy on 2009-02-03
Whenever you see the kernel coming, be happy you are a duck! :p

---

### Post by druellan on 2009-02-03
BTW, how MACOS´s kernel suits here? My a appreciation is that its an unix-based microkernel with kernel-modules attached to it?

> **Grant A. said:**
> Here is a nice little diagram of the origins:
Mmm, Minix is a stand alone project?

---

### Post by handy on 2009-02-03
> **druellan said:**
> BTW, how MACOS´s kernel suits here? My a appreciation is that its an unix-based microkernel with kernel-modules attached to it? 

You will get more than you want from this link:

*_[http://www.kernelthread.com/mac/osx/arch_xnu.html](http://www.kernelthread.com/mac/osx/arch_xnu.html)_*

---

### Post by CrazyArcher on 2009-02-03
> **druellan said:**
> Mmm, Minix is a stand alone project?
Pretty much so. It was built for educational purposes.

---

### Post by Sorivenul on 2009-02-03
> **CrazyArcher said:**
> Pretty much so. It was built for educational purposes.
Originally, yes, and it still is used as such, though in theory MINIX3 was supposed to focus more on a true usability aspect. I haven't noticed much difference from the two on the user level. Other people's experiences may vary.

---

### Post by druellan on 2009-02-03
> **handy said:**
> *_[http://www.kernelthread.com/mac/osx/arch_xnu.html](http://www.kernelthread.com/mac/osx/arch_xnu.html)_*
Thanks.

---

### Post by orethrius on 2009-02-03
> **myromance123 said:**
> Sorivenul,

  That page is hilarious xD
I was expecting a read-100-times-to-understand explanation of the matter, and all it uses is a  DUCK!

 Very Cool~

That's pretty much the jist of the matter.  If it functions like Unix proper, it can be classified as "Unix-like".

As for Minix and Linux being "independent" systems: no system exists in a vacuum.  [Linus Torvalds had (has) many talks with Andrew Tanenbaum](http://www.nationmaster.com/encyclopedia/Andrew-S.-Tanenbaum) on USENET comp.os mailing lists.  The codebase is where those similarities begin and end.  :)

---

### Post by Grant A. on 2009-02-03
> **Sorivenul said:**
> Originally, yes, and it still is used as such, though in theory MINIX3 was supposed to focus more on a true usability aspect. I haven't noticed much difference from the two on the user level. Other people's experiences may vary.

I remember there being a project dedicated to KDE and GNOME ports to MINIX3 a couple years ago. I wonder where those went.

---

### Post by Sorivenul on 2009-02-03
> **Grant A. said:**
> I remember there being a project dedicated to KDE and GNOME ports to MINIX3 a couple years ago. I wonder where those went.
Good question, as even TWM/X on MINIX3 has proven next to unusable in my tests.

---

### Post by fistfullofroses on 2009-02-04
> **gjoellee said:**
> Windows has used the Windows NT kernel since Windows NT was released.

Not quite. The Windows 4.x kernel was in use through ME, which was released long after NT. NT was more a contemporary of Windows 95. 95, 95 Second Release, 98, 98SE, and ME were all running the Win4.x kernel series. NT itself was built upon OS/2 which in-turn was built upon QNX. NT kernels were used in 2k, XP, 2k3, and somewhat in Vista. Win7 uses a microkernel of some sort, which was running next to NT style kernel in Vista (hence making Vista's drivers usable in Win7). I am thinking the Windows 7 will be the basis of Windows iterations for possibly the next 10 years.

---

### Post by albinootje on 2009-02-04
> **fistfullofroses said:**
> Not quite. The Windows 4.x kernel was in use through ME, which was released long after NT. NT was more a contemporary of Windows 95. 95, 95 Second Release, 98, 98SE, and ME were all running the Win4.x kernel series. NT itself was built upon OS/2 which in-turn was built upon QNX. NT kernels were used in 2k, XP, 2k3, and somewhat in Vista. Win7 uses a microkernel of some sort, which was running next to NT style kernel in Vista (hence making Vista's drivers usable in Win7). I am thinking the Windows 7 will be the basis of Windows iterations for possibly the next 10 years.

Good that you added this information, I didn't want to respond as a non-Windows user :)

But I suspect the "built upon QNX" is not correct.
Qnx was a closed source OS since years, and I've never read about any link between MS-Windows NT or OS/2 with Qnx.
Perhaps you are confused it with VMS ? I've read that one well-known VMS developer moved to Microsoft and started working on NT.

See here for more information :
[http://en.wikipedia.org/wiki/Windows_NT](http://en.wikipedia.org/wiki/Windows_NT)
[http://en.wikipedia.org/wiki/Os/2](http://en.wikipedia.org/wiki/Os/2)
[http://en.wikipedia.org/wiki/Qnx](http://en.wikipedia.org/wiki/Qnx)
[http://en.wikipedia.org/wiki/OpenVMS](http://en.wikipedia.org/wiki/OpenVMS)

---

### Post by namegame on 2009-02-04
> **fistfullofroses said:**
> 
MINIX3, Fiwix, UNIX, BSD, Linux, Solaris, AIX, HP-UX, Linux-libre, RISCOS, GNU, OS X, Next, IRIX, Ultrix, Tru64, and Xenix are all consider Unix-like systems.



I'm not so sure that this is correct. Solaris, AIX, HP-UX, Mac OS X, etc, all pass the Single Unix Specification. They are even listed as Unix 03 compliant. (Full compliance) As such, they should be called Unix, not "Unix-like." Ubuntu, Fedora, the *BSDs, are all "Unix-like."

---

### Post by Sorivenul on 2009-02-04
> **namegame said:**
> Solaris, AIX, HP-UX, Mac OS X, etc, all pass the Single Unix Specification. They are even listed as Unix 03 compliant. (Full compliance) As such, they should be called Unix, not "Unix-like." Ubuntu, Fedora, the *BSDs, are all "Unix-like."
This is pretty much it, in a nutshell. I still call the BSDs Unices though. See my [previous post]("http://ubuntuforums.org/showpost.php?p=6655655&postcount=7") regarding NetBSD and ducks.

---

### Post by namegame on 2009-02-04
> **Sorivenul said:**
> This is pretty much it, in a nutshell. I still call the BSDs Unices though. See my [previous post]("http://ubuntuforums.org/showpost.php?p=6655655&postcount=7") regarding NetBSD and ducks.

Do you know if they aren't considered Unix because they didn't pass "the test" or if they haven't submitted themselves for review?

The cost of certification can be quite expensive. [http://www.opengroup.org/openbrand/Brandfees.htm](http://www.opengroup.org/openbrand/Brandfees.htm)

---

### Post by albinootje on 2009-02-04
> **namegame said:**
> Do you know if they aren't considered Unix because they didn't pass "the test" or if they haven't submitted themselves for review?

The cost of certification can be quite expensive. [http://www.opengroup.org/openbrand/Brandfees.htm](http://www.opengroup.org/openbrand/Brandfees.htm)

When looking at "UNIX" as in looking at POSIX compliant, see here : [http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

> 
Fully POSIX-compliant

The following operating systems conform (i.e., are 100% compliant) to one or more of the various POSIX standards.

    * A/UX
    * AIX
    * BSD/OS
    * HP-UX
    * INTEGRITY
    * IRIX
    * LynxOS
    * Mac OS X v10.5
    * MINIX
    * MPE/iX
    * QNX
    * RTEMS (POSIX 1003.1-2003 Profile 52)
    * Solaris
          o OpenSolaris
    * UnixWare
    * velOSity
    * VxWorks (IEEE Std. 1003.13-2003 PSE52; see [http://get.posixcertified.ieee.org/cert_prodlist.tpl](http://get.posixcertified.ieee.org/cert_prodlist.tpl))


---

### Post by Sorivenul on 2009-02-04
> **namegame said:**
> Do you know if they aren't considered Unix because they didn't pass "the test" or if they haven't submitted themselves for review?

The cost of certification can be quite expensive. [http://www.opengroup.org/openbrand/Brandfees.htm](http://www.opengroup.org/openbrand/Brandfees.htm)
Providing free operating systems with a limited team of core devopers, licensing fees can get expensive. This to me, seems the biggest issue, and as far as the BSDs are concerned, I don't think they especially care about certification anymore. Especially when it is simply a matter of following a specification and being "branded". The BSD systems, "genetically", are Unices and stem from the orginal designs of AT&T UNIX, though today they possess little to no common code. 

If you know you come from royalty, does it really matter that much that you have bloodtests done just to certify it?

EDIT:
> **albinootje said:**
> When looking at "UNIX" as in looking at POSIX compliant, see here : [http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)
The POSIX standard is and its involvement with the SUS can be a confusing topic. In general, I find ["Not by UNIX Alone"]("http://www.ibm.com/developerworks/power/library/pa-spec13/index.html") and the [History of Unix Standardization]("http://www.faqs.org/docs/artu/ch17s02.html") by Eric Raymond to be a bit more comprehensive than the Wikipedia article.

---

### Post by ezsit on 2009-02-04
> NT was more a contemporary of Windows 95. 95, 95 Second Release, 98, 98SE, and ME were all running the Win4.x kernel series. NT itself was built upon OS/2 which in-turn was built upon QNX.

I am sorry to say, you know nothing of Windows development. NT was started as OS/2 V3 to be built specifically for the 386 chip and to be a microkernel, portable operating system. Once Microsoft and IBM split up, Microsoft's OS/2 V3 changed names to Windows NT. OS/2 has nothing to do with QNX, these were separate operating systems developed independently by different companies and share NO similarity.

OS/2 started life as a 16 bit replacement operating system for DOS that in 1985-86 began with IBM and Microsoft jointly developing parts of the operating system. IBM took over complete development responsibility in 1989-90 with release OS/2 1.3. MS may have had rights to distribute OS/2 1.3, but by that time it was an IBM product. OS/2 2.0, 3.0 and 4.0 were gradually rebuilt with many 32 bit components, but much of the kernel remained 16 bit assembler code specific to the x86 architecture. IBM tried to make OS/2 a microkernel operating system to run on the PowerPC chip back in the mid 1990's to be used as the basis for a joint project with Apple for the next generation Macs. This never happened.

QNX was developed by a Canadian company as a realtime operating system to run on x86 cpus. QNX 1.x and 2.x were 16bit and QNX 4 and beyond are 32bit operating systems used primarily in embedded devices. QNX has a PC operating system, but this really only exists as a development platform for embedded operating systems.

Windows 95, 98, and ME were all based on DOS with an increasing amount of 32 bit code, primarily in the drivers. By the time ME was released, there was very little DOS code left in these consumer versions of Windows. Windows NT began development under the project name OS/2 version 3. but once IBM and Microsoft split-up, MS renamed the project to Windows NT. The NT kernel still exists in Windows Vista as technically, Vista is Windows NT 6. Windows 7 is the next step in the development. Windows NT began with 3.1, then 4.0, then Windows 2000 (NT 5), Windows XP (NT 5.5?) then Vista (NT 6). That is why Windows 7 is named Windows 7.

I have run every version of OS/2 from 1.3 through 4.0 and can attest to it being completely different from Windows NT, which I ran from versions 3.51 through XP. I have used MS-DOS 4.0 through PC-DOS 7. I have installed and used QNX 6.0 through 6.23 and can tell you there is NO similarity to anything else on the market of consumer operating systems.

---

### Post by jrusso2 on 2009-02-04
Microsoft hired David Cutler from Digital to do the NT program.  He brought with him the team for Digital that was responsible for VaxVMS which he also designed. 

They say the original NT is much closer to VAX then anything and for a long time Cutler was accused of using Digital code in NT.  But since NT is not open source its hard to prove.  The only non Microsoft company with a copy of that code is Citrix.

---

### Post by handy on 2009-02-04
> **jrusso2 said:**
> 
They say the original NT is much closer to VAX then anything and for a long time Cutler was accused of using Digital code in NT.  But since NT is not open source its hard to prove. 

I expect I'm not alone in thinking that the reason MS will never open much of their code is due to its origins.

---

### Post by ezsit on 2009-02-05
The NTFS filesystem was supposedly a very close copy of the VAX filesystem, Files-11. I remember the first company to release a filesystem utility for Windows NT 3.1, a defragger, was Diskeeper. Before the release of Windows NT, the makers of Diskeeper were primarily in the business of writing VAX VMS software, specifically, disk and filesystem utilities. Coincidence? I think not.

---

### Post by fistfullofroses on 2009-02-06
> **ezsit said:**
> I am sorry to say, you know nothing of Windows development. NT was started as OS/2 V3 to be built specifically for the 386 chip and to be a microkernel, portable operating system. Once Microsoft and IBM split up, Microsoft's OS/2 V3 changed names to Windows NT. OS/2 has nothing to do with QNX, these were separate operating systems developed independently by different companies and share NO similarity.

OS/2 started life as a 16 bit replacement operating system for DOS that in 1985-86 began with IBM and Microsoft jointly developing parts of the operating system. IBM took over complete development responsibility in 1989-90 with release OS/2 1.3. MS may have had rights to distribute OS/2 1.3, but by that time it was an IBM product. OS/2 2.0, 3.0 and 4.0 were gradually rebuilt with many 32 bit components, but much of the kernel remained 16 bit assembler code specific to the x86 architecture. IBM tried to make OS/2 a microkernel operating system to run on the PowerPC chip back in the mid 1990's to be used as the basis for a joint project with Apple for the next generation Macs. This never happened.

QNX was developed by a Canadian company as a realtime operating system to run on x86 cpus. QNX 1.x and 2.x were 16bit and QNX 4 and beyond are 32bit operating systems used primarily in embedded devices. QNX has a PC operating system, but this really only exists as a development platform for embedded operating systems.

Windows 95, 98, and ME were all based on DOS with an increasing amount of 32 bit code, primarily in the drivers. By the time ME was released, there was very little DOS code left in these consumer versions of Windows. Windows NT began development under the project name OS/2 version 3. but once IBM and Microsoft split-up, MS renamed the project to Windows NT. The NT kernel still exists in Windows Vista as technically, Vista is Windows NT 6. Windows 7 is the next step in the development. Windows NT began with 3.1, then 4.0, then Windows 2000 (NT 5), Windows XP (NT 5.5?) then Vista (NT 6). That is why Windows 7 is named Windows 7.

I have run every version of OS/2 from 1.3 through 4.0 and can attest to it being completely different from Windows NT, which I ran from versions 3.51 through XP. I have used MS-DOS 4.0 through PC-DOS 7. I have installed and used QNX 6.0 through 6.23 and can tell you there is NO similarity to anything else on the market of consumer operating systems.

I understand that they are different "operating systems," and I think that the games of symantics is at work here. First, much of the code for the NT kernel (note that a kernel alone does not comprise and OS) is from the OS/2 kernel. While a system does evolve it does not change completely, and the elimination of code does not makes something completely different. I also want to ask: how can you get the code for ME when ME is closed source, and therefore how can you say that not much DOS code still exists in it? This is puzzling. Further, apps can still directly access hardware (as opposed to passing that to a kernel and then on to the hardware, or passing to a HAL layer) which is very DOS-like. Secondly, I guess I not have said that it was based upon QNX, and opted to say, more accurately, that many parts of the OS/2 kernel were supposedly modeled in a similar fashion (whether this is true or not, I cannot accurately say. I was told this by a friend of mine who worked at IBM through that era).

I too have used OS/2, DOS, Windows, BSD, and Linux operating systems. You're not impressing anyone there. This is the "other OS" board. You ought to be a bit less condescending. Next, the Vista kernel architecture does use a bit of NT code, and is indirectly a descendant, but it changes quite a few things. First, in previous versions of Windows the kernel was largely monolithic, and quite a few parts of the OS ran in kernel space. Vista breaks that mold, and runs quite a bit more in user space. Much of the I/O control was also completely rewritten. Does this constitute a break? Next, Win7 uses a much more micro-kernel like design, and from usage seems to be similar with driver handling to MINIX3. Does this constitute a new kernel? Where do you draw the line? Are we to say the BSD is a totally UNIX kernel because it's origins are the same, or can we safely say that while being "UNIX spec compliant" it is not the same kernel as the last UNIX release (UNIX V7 if I am not mistaken)? Or for the matter should we say that since OS/2 and NT started in the same place they are the same kernel?

---

### Post by ezsit on 2009-02-07
> I understand that they are different "operating systems," and I think that the games of symantics is at work here. First, much of the code for the NT kernel (note that a kernel alone does not comprise and OS) is from the OS/2 kernel. While a system does evolve it does not change completely, and the elimination of code does not makes something completely different.

Much of the NT kernel is NOT from the OS/2 kernel. The last OS/2 kernel that Microsoft had access to was from OS/2 1.2 - a 16 bit operating system and Windows NT was written from the ground up as a 32 bit operating system. The OS/2 kernel contained a lot of assembler code specific to the x86 architecture. NT's kernel was built from the start to be portable across at least four different CPU archtectures (x86, MIPS, PowerPC, and Alpha). 

Windows NT was released with some OS/2 DLL libraries to provide some backwards compatibility with older 16 bit OS/2 command line programs, but that's about it. Windows NT also included some POSIX compatibilty, but does not make the kernel a Unix derived kernel. Oh, and Windows NT included an HPFS filesystem driver so NT users could migrate their OS/2 data over to NT boxes. Neither the filesystem drivers nor the OS/2 compatibility DLLs were integral to the kernel though.

> Next, the Vista kernel architecture does use a bit of NT code, and is indirectly a descendant, but it changes quite a few things. First, in previous versions of Windows the kernel was largely monolithic, and quite a few parts of the OS ran in kernel space.

"Indirectly?" The Vista kernel is the evolved NT kernel. The NT kernel was released in 1992 and has seen continuous development to the present day. The original NT kernel from Windows NT 3.1 was actually more microkernel-inspired than the current versions. If we are to believe Microsoft, the Windows 7 kernel is "getting back to its roots" and going microkernel again. We will never really know. However, even at its release when Microsoft said the NT architecture was microkernel, it was never a true microkernel.

As for trying to impress people, I don't feel the need. I was just responding to an obviously flawed posting. I would not want younger readers to walk away misinformed.

BTW:
> Or for the matter should we say that since OS/2 and NT started in the same place they are the same kernel?
What? I don't even know where to begin with this gem. Please, if nothing else, check Wikipedia for OS/2 and Windows NT.

---

### Post by myromance123 on 2009-02-12
Handy, you made me laugh XD
  Be glad you're a duck, lol.

So a kernel is part of an OS.
  Holy COW !!
fistfullofroses,
there are so many different systems you named! I feel like I have been living in the dark. Wow  O.o

Thanks Mason Whitaker for trying to make it more understandable for me.

I'm gonna read into this so called POSIX standard. Interesting.

Sad to say I stopped reading at page 4, it turned into uncertainties when reading all those different statements but nonetheless I am grateful for all your responses.

 One thing I noted was how much all of you referenced wikipedia for information. I was not sure if I could trust wikipedia but it seems it is not as outdated as I thought in the computer related department.

  Thank You ~ :)

---

### Post by oasmar1 on 2009-02-12
Is Windows 7 a microkernel? I always thought of the NT Kernel as more of a mix (slightly more monolithic than micro). If Windows 7 is a microkernel, are they saying it is completely Micro or just more Micro than Monolithic?

---

