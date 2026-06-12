---
title: "Some unresolved issues about platform-specific cross-compiling"
date: 2010-05-12
forum: Packaging and Compiling Programs
---

### Post by qyot27 on 2010-05-12
I know that MinGW provides the necessary parts of the Windows API to allow for cross-compiling, or its main purpose to allow POSIX-compliant binaries to be built natively on Windows.  But what about a system that already *has* a native variant of GCC available?  I'm talking about OS X - Apple provides their own version of GCC 4.2 through Xcode (and has the source code for it on [opensource.apple.com](http://www.opensource.apple.com/release/developer-tools-322/)), and MacPorts ostensibly allows one to even get GCC 4.4 running natively on OS X, although I've not tried that yet.

So theoretically, if I wanted to cross-compile for OS X under Ubuntu (or heck, Windows - I use MinGW/MSys for native compilation there anyway; what's another cross-compiler?), is getting that version of GCC to build all that's required plus those vital parts from Darwin?  [README.Apple](http://www.opensource.apple.com/source/gcc/gcc-5659/README.Apple) mentions this at the very bottom of the page, although I'm sure that's more aimed toward those on Snow Leopard compiling an x86 version of GCC rather than users on non-OSX/Darwin operating systems.

While I certainly would *like* to know how to compile Apple-GCC and the Apple-binutils myself (all my compiling experience thus far is for just a few select apps that are nowhere on the level of GCC or the Linux kernel), I don't want to try and possibly succeed to build it only to find out that cross-compiling with it is impossible because it's missing other vital system components (if the lack of said components doesn't cause the build process for GCC to fail as well).

Finally, if this actually succeeds, what are the chances of such a solution making its way into the repositories like MinGW has?  Where would I need to go to suggest its inclusion?  The Maverick testing forum, mailing list, IRC, Launchpad?  Not my build(s), of course, but if it can be done, then IMO it would be worth suggesting for inclusion.  Unless this has already been done through a PPA or something and I just don't know where to look.  Any help on that front would be appreciated, too.

---

