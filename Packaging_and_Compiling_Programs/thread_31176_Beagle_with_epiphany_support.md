---
title: "Beagle with epiphany support"
date: 2005-05-02
forum: Packaging and Compiling Programs
---

### Post by jonny on 2005-05-02
Hi

I'm trying to compile Beagle from CVS according to the instructions in the wiki.  I want to compile in Epiphany support (Epiphany is a quietly addictive, seriously underrated browser, and I don't want to go back to Firefox), but I get this error message when I try running ./autogen.sh --prefix=/usr/local```
epiphany-1.2 >= 1.2.1... Package epiphany-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `epiphany-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'epiphany-1.2' found
```I have Epiphany 1.6, and can't find an epiphany-1.2 package anywhere despite extensive (but possibly inept!) googling.

Is there away around this?  Can I create a symbolic link somewhere to trick the system into thinking epiphany-1.2 exists.  Or do I just have to get patient and wait for Beagle to mature a little?

---

