---
title: "makefile.am"
date: 2008-10-11
forum: Programming Talk
---

### Post by Rich78 on 2008-10-11
I understand what it's there for but how are these files generate?  From scratch or a tool?

Thanks

---

### Post by snova on 2008-10-11
*You* write the Makefile.am's. Automake uses them to generate Makefile.in's. The configure script processes those to generate Makefiles.

There is a tool to write these for you, but I think it's meant to initialize everything when you're setting up your project.

From scratch, then, is the answer.

Are you sure you want to use Autotools? I found them a little messy. Look into alternative systems before you decide on this. CMake, for one, is gaining popularity; and I personally like SCons.

---

### Post by Rich78 on 2008-10-11
No not particularly just that I came across it in some open source code I wish to port to my Mac.

Thanks

---

### Post by PandaGoat on 2008-10-11
Macs comes with GNU autotools so it can handle makefiles and all that.

---

