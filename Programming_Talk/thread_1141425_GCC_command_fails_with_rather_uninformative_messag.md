---
title: "GCC command fails with rather uninformative message"
date: 2009-04-28
forum: Programming Talk
---

### Post by arathel on 2009-04-28
I am accessing an ARM platform via Putty over Telnet and this is a direct copy of my buffer:

-------------

/mnt/root/home/source # vim st.c


int main (void)
{
return 0;
}

~
~
~
"st.c" 7L, 33C written

/mnt/root/home/source # gcc st.c
Aborted

---------------

GCC version is 4.1.2. The ARM platform is running Debian.
As you can see, gcc quits on me with "Aborted", no further information.
Any suggestions?

---

### Post by dwhitney67 on 2009-04-28
I am not familiar with an ARM system, but your problem appears as if you are having trouble accessing the appropriate gcc compiler for that architecture.  Can you verify that you are indeed running the appropriate gcc compiler?  A simple command such as 'which gcc' should suffice.

If the result is what you expect, then verify that you have the PATH and libraries setup correctly.

---

### Post by arathel on 2009-04-28
"which gcc" points to /usr/bin/gcc

"gcc -dumpmachine" reports "arm-linux-gnu" which is also expected.

---

### Post by dwhitney67 on 2009-04-28
Since you are logging into /mnt/root/home/source, I would have expected your gcc to be somewhere in that area, possibly /mnt/root/usr/bin.

EDIT:  I wonder if you need to run 'chroot' to /mnt/root?

---

### Post by arathel on 2009-04-28
I should've noticed that myself.

Anyway, tried and the problem persists (the system's root is mounted on /mnt/root) and "/" is link into that same folder. Wierd, I know, but then again, its factory defaults that I never changed (spent over 2 days searching through startup scripts just to get rw on /var).

If its relevant, its the TS7390 ([http://www.embeddedarm.com/products/board-detail.php?product=TS-7390#](http://www.embeddedarm.com/products/board-detail.php?product=TS-7390#))

I also tried the "-v" swich on GCC. It *should* output the commands issued by gcc, but intead does the same as "-V" which outputs version. If the gcc team changed that option, they fergot to update the --help text.

Lastly, the "-S" option (compile only, do not link) goes through. and I get the ASM file corresponding to the .c code. As such I assume the error is in trying to link. Since, however the program has no includes (and therefore no dependencies) leads me to belive its the assembler that fails to be called. This is beyond my knowledge. Any tips?

---

### Post by dwhitney67 on 2009-04-28
Actually, the -c option is for compile-only, and generates an object file.  The -S generates assembly code.

Regardless, I empathize with your dilemma.  I recently (and still do!) have a similar problem when manually attempting to cross-compile with the 'gcc' for a MontaVista distro.  Eclipse (DevRocket) can do it without issues, but when I attempt to manually build the s/w using the command line, the linker seg-faults on me.

It must have something to do with the LD_LIBRARY_PATH or something similar.  I suspect that when I attempt to call the linker, that it is referencing libraries that are part of my CentOS distro, not MontaVista's.

Anyhow, I detest using Eclipse, and would love to sort out the issue so that I can manually build the s/w products from the command-line, but for now that "project" is on hold.

Do you have a /mnt/root/bin/bash file?  If you do, maybe you can goto /mnt/root, and then run "chroot .".  You will need root-privileges to do that.

---

### Post by johnl on 2009-04-28
Check that all the necessary binutils are there and are for the appropriate targets; run the following with "-v":

as
gcc
ld

Might also check for:

ar
nm
objdump
ranlib
strip

---

### Post by Arndt on 2009-04-28
> **johnl said:**
> Check that all the necessary binutils are there and are for the appropriate targets; run the following with "-v":

as
gcc
ld

Might also check for:

ar
nm
objdump
ranlib
strip

Perhaps using 'strace' gives some useful information?

---

