---
title: "Help for prefined constants?"
date: 2009-06-22
forum: Programming Talk
---

### Post by charliep51 on 2009-06-22
I have noticed that, on Ubuntu, shutdown() does not really cause the local port of the socket to be reusable, even though both server and client execute shutdown()/close().  This works on other native Linux installations.  I can work around the problem, but I would prefer to have the workaround code enclosed in some appropriate #ifdef.  On Cygwin, the appropriate predefined constant is "__CYGWIN__".  Is there any analogous constant defined for Ubuntu?  Or do I have to make special purpose Makefile defines?

Thanks in advance for any help,
Charlie P.

---

### Post by jinksys on 2009-06-23
> **charliep51 said:**
> I have noticed that, on Ubuntu, shutdown() does not really cause the local port of the socket to be reusable, even though both server and client execute shutdown()/close().  This works on other native Linux installations.  I can work around the problem, but I would prefer to have the workaround code enclosed in some appropriate #ifdef.  On Cygwin, the appropriate predefined constant is "__CYGWIN__".  Is there any analogous constant defined for Ubuntu?  Or do I have to make special purpose Makefile defines?

Thanks in advance for any help,
Charlie P.

I assume that whoever compiles the code will know that the program is being built specifically for Ubuntu, so wouldn't a 'gcc -D UBUNTU' suffice?

---

### Post by charliep51 on 2009-06-23
Well, yes of course that does work.  But I have a pile of code and Makefile and all of that for quite a few systems, and it would be nice if I could just copy the directory from place to another without having to hand-edit the files.

My current solution is to enclose the Makefile in a shell script which (a) calls "uname -a", (b) extracts something distinctive (e.g., "ubuntu"), (c) in a case statement, define an environmental variable, e.g. EXTRA_CFLAGS=-D__UBUNTU__, and (d) invokes make -e which contains a redefinition for ${CFLAGS} to incorporate EXTRA_CFLAGS.

But I thought Ubuntu might be nice enough to obviate the need for all of that.

Regards,
Charlie P.

---

