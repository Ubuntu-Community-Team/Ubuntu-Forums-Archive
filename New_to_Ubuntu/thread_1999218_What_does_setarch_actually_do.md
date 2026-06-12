---
title: "What does setarch actually do?"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by venom104 on 2012-06-07
I had the infamous diablo 3 problem, stuck at retrieving hero list. What fixed it was this setarch i386 -3 -L -B -R wine '/media/windows/Program Files (x86)/Diablo III/Diablo III.exe'-launch -opengl 

Anyway, the man page says this...

    setarch  -  change reported architecture in new program environment and
       set personality flags


DESCRIPTION
       setarch This utility currently only affects the output of uname -m. For
       example,  on an AMD64 system, running 'setarch i386 program' will cause
       'program' to see i686 (or other relevant arch)  instead  of  x86_64  as
       machine  type.  It  also allows to set various personality options. The
       default program is /bin/sh.


I don't understand why this is needed at all. Doesn't a 64 bit system have an emulation environment for x86 programs? What does this actually do that causes the bug to go away?

---

### Post by idoitprone on 2012-06-07
> **venom104 said:**
> I had the infamous diablo 3 problem, stuck at retrieving hero list. What fixed it was this setarch i386 -3 -L -B -R wine '/media/windows/Program Files (x86)/Diablo III/Diablo III.exe'-launch -opengl 

Anyway, the man page says this...

    setarch  -  change reported architecture in new program environment and
       set personality flags


DESCRIPTION
       setarch This utility currently only affects the output of uname -m. For
       example,  on an AMD64 system, running 'setarch i386 program' will cause
       'program' to see i686 (or other relevant arch)  instead  of  x86_64  as
       machine  type.  It  also allows to set various personality options. The
       default program is /bin/sh.


I don't understand why this is needed at all. Doesn't a 64 bit system have an emulation environment for x86 programs? What does this actually do that causes the bug to go away?

setarch just tells the operating system which architect to run the program. Almost all x86_64 cpus have a built in 32 bit x86 built right in.

It should not matter because wine is only designed to run 32bit only applications. In fact your should have 32 binaries in your ubuntu.

The important thing is not the setarch but those switches.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953)

One commenter said there actually a memory bug in Diablo 3. To fix it you have to make sure the program only addresses 32 bit address space.

Those set arch switches are meant as a workaround for the bug

-3 force the app to use only up to 3GB

-L change the address space layout

-B   this switch limits address space to 32bits 

-R Remove address space randomization - helps get rid of some problems when the app expect a function to be at a certain address space.

---

