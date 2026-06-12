---
title: "Compiling the OSS components of NX from NoMachine"
date: 2008-04-14
forum: Packaging and Compiling Programs
---

### Post by eracks on 2008-04-14
Hey everyone.  I'm not sure if anyone else has tried to do this on an Ubuntu machine, but I'm trying to get the OSS components of NoMachine's NX server compiled and have run into some problems.

For those who are familiar with this, my problem arises when I try to build the NX server's custom XFree86 distribution.  The build itself goes smoothly (I'm compiling under the nx-X11 subdirectory), but when I try a make install, I get the following errors:

Events.c: In function 'nxagentDispatchEvents':
Events.c:538: warning: implicit declaration of function 'XCheckIfEventNoFlush'
Events.c: In function 'nxagentHandleXFixesSelectionNotify':
Events.c:2405: error: 'SelectionCallback' undeclared (first use in this function)
Events.c:2405: error: (Each undeclared identifier is reported only once
Events.c:2405: error: for each function it appears in.)
Events.c:2415: error: 'SelectionInfoRec' undeclared (first use in this function)
Events.c:2415: error: expected ';' before 'info'
Events.c:2451: error: 'info' undeclared (first use in this function)
make[4]: *** [Events.o] Error 1
make[3]: *** [hw/nxagent] Error 2
make[2]: *** [install] Error 2
make[1]: *** [install] Error 2
make: *** [install] Error 2

If anyone has run into this problem, and knows how to solve it, please let me know.  Thanks!

James
--
eRacks Open Source Systems
[http://www.eracks.com/](http://www.eracks.com/)

---

### Post by uptimebox on 2008-04-19
I have exactly the same problem on Debian Etch, so I don't think it's Ubuntu-specific bug.

---

### Post by uptimebox on 2008-04-19
I solved the problem. In my case, it was caused by extracting unnesesary archive nx-X11-compat-3.2.0-1.tar.gz to source tree. When i strictly followed instructions at [http://www.nomachine.com/documentation/building-components.php](http://www.nomachine.com/documentation/building-components.php) everything went fine.

---

