---
title: "(newbie) how to have more than one gcc compiler version?"
date: 2011-11-14
forum: Packaging and Compiling Programs
---

### Post by jmborr on 2011-11-14
Dear Ubuntu users,

I have gcc 4.6.1 in my ubuntu oneiric. It turns out some code I have to compile requires an older version of gcc.

- Where do I get an older compiler, and how do I install it i ubuntu 11.10?

- Will I have future troubles deriving from having two gcc compiler versions in my distro? I'm quite an ignorant here, please be understanding.

Jose

---

### Post by Bachstelze on 2011-11-14
Which version of gcc do you need?

---

### Post by jmborr on 2011-11-15
> **Bachstelze said:**
> Which version of gcc do you need?

It turns out the developers had a bunch of bugfixes for the errors I had, so I applied the patches and now it compiled. 

Thank you for answering my message, and I'm sorry for the trouble!

---

### Post by qyot27 on 2011-11-15
For future reference, though, you just look for the right version in the repositories - packages for gcc-4.4 (provides 4.4.6) and gcc-4.5 (provides 4.5.3) are both there.

When you go to compile, the program may have a special parameter to use for that purpose (like --cross-prefix) or you'd use the right environment variable(s) to force the use of an older version of the compiling tool(s), like this:
CC=gcc-4.4 ./configure

---

### Post by jmborr on 2011-11-15
> **qyot27 said:**
> For future reference, though, you just look for the right version in the repositories - packages for gcc-4.4 (provides 4.4.6) and gcc-4.5 (provides 4.5.3) are both there.

When you go to compile, the program may have a special parameter to use for that purpose (like --cross-prefix) or you'd use the right environment variable(s) to force the use of an older version of the compiling tool(s), like this:
CC=gcc-4.4 ./configure

Thanks for the tips!

---

