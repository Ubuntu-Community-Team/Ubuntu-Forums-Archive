---
title: "Finding Dependencies For Programs"
date: 2008-10-13
forum: Packaging and Compiling Programs
---

### Post by JustYakov on 2008-10-13
Hello everyone!

I tried to make a .deb package (named **mbg**), but testing with lintian resulted in this error:

> W: mbg: missing-depends-line

According to the lintian website, it means that I have a binary file but did not specify any dependencies. The program that I'm suppling is a compiled Perl script.

So here's my question: is there a program to find what are the dependencies for a program? (*dpkg-shlibdeps* doesn't seem to work) Or should I keep the program uncompiled?

Thank you in advance.

---

### Post by Sef on 2008-10-14
Moved to  [Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44").

---

### Post by InfinityCircuit on 2008-10-14
A perl script should still have Depends: ${shlibs:Depends} in debian/control.

---

### Post by JustYakov on 2008-10-14
Thanks for the reply.

I'm not sure that the compiled Perl script has dependencies because I actually ran it on my server. It seemed to go fine except the part it tried to run on a GUI.

The only reason I'm posting this is to "satisfy" lintian, however that didn't work very well. So what I've decided to do is not to compile the script, however it will require some packages to do the job. Even after that, lintian wasn't very happy, but I don't care.

In any case, once again, that you for your reply.

---

