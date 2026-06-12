---
title: "the weird thing about apple and mac os"
date: 2007-10-05
forum: Other OS Talk
---

### Post by arkara on 2007-10-05
so i know that apple mac os is a very very friendly linux distro based on open bsd...
so is it able to run mac os programs on other linux distros?????
for example microsoft office for mac?

---

### Post by tgalati4 on 2007-10-05
Mac OS X is based on BSD, so technically it's not Linux.  Applications in Mac OS X use Cocoa and the Quartz rendering/compositing software.  This makes porting difficult because although the underlying operating system is open source (Darwin-->OpenDarwin) the graphical server (Cocoa/Quartz) is not based on X (xfree86 or xorg) and is proprietary.  The window manager is called Aqua and that is proprietary.

The closest thing is to buy an Intel Mac and run OS X and run virtualized sessions of Windows or Ubuntu/Linux.  

The Mac OS is so closely tied to the hardware that porting it to another platform is difficult.

---

### Post by Sef on 2007-10-05
> so i know that apple mac os is a very very friendly linux distro based on open bsd...

Apple is derived from Unix itself.   GNU/Linux is a clone of Unix.

> so is it able to run mac os programs on other linux distros?????

If the program is derived from Unix, with modifications possibly.

> for example microsoft office for mac?

No.  But with WINE, you can.

---

### Post by Incense on 2007-10-05
The short answer is OSX native apps only run on OSX.

---

### Post by maybeway36 on 2007-10-06
Parts of Mac OS are derived from FreeBSD, actually. Darwin came from NEXTSTEP.

---

### Post by fistfullofroses on 2007-10-06
Hypothetically, with a ton of elbow grease you could port MacOS programs to Linux. However, in the case of MS Office, the source is not available. Also, you would be breaking the law if you modified MS Office... so no. You cannot run Office for Mac on Linux.

---

### Post by aysiu on 2007-10-06
Mac OS X isn't really that much "friendlier" than the most popular Linux distributions.

---

### Post by faraaz on 2007-10-09
@aysiu: I agree...IMO Ubuntu is a lot more intuitive than Mac OS X...

---

### Post by happysmileman on 2007-10-09
> **Incense said:**
> The short answer is OSX native apps only run on OSX.

If apple is based on OpenBSD kernel, then in theory shouldn't it have binary compatibility with console programs compiled for OpenBSD? While C may link to libraries on one OS that aren't on another, if you used ASM making system calls could you make a program that would work natively on both?

Not practical at all, but just curious

---

### Post by 3rdalbum on 2007-10-10
> **happysmileman said:**
> If apple is based on OpenBSD kernel, then in theory shouldn't it have binary compatibility with console programs compiled for OpenBSD? While C may link to libraries on one OS that aren't on another, if you used ASM making system calls could you make a program that would work natively on both?

Not practical at all, but just curious

I believe I know less about the internals of systems than you do, as some of what you said went over my head :-)

But FreeBSD, other BSDs and Unixes, and Linux; all use ELF as their executable format. Mac OS X doesn't understand ELF. So in terms of direct binary compatibility, I don't think you could have a precompiled program that works on Mac OS X and FreeBSD.

People make too much of the relationship between Darwin and FreeBSD. It's like saying that I can write awesome science fiction just because H.G. Wells was a distant relative of mine. The relationship is too distant. The kernel itself is a mishmash of NextStep, ancient FreeBSD code, and more recent Apple code (plus binary blobs from Apple and hardware manufacturers). The userspace consists of heavily-hackedup versions of the FreeBSD userspace tools. Then the GUI layer and the Apple services are placed on the top.

I think the reason why nobody has embarked on a "MINE" project is because the task would be enormous, and would probably work even less well than WINE.

---

### Post by tgalati4 on 2007-10-10
Going the otherway however seems to be easier.  Using Fink Commander, there is a growing body of open source packages that have been ported to the native Mac OS X environment.  These packages look good and generally run well under Tiger.

There are many precompiled binaries already available.  What's not precompiled is available for compiling from source, although I've only had 50% success because of depencency hell.

---

