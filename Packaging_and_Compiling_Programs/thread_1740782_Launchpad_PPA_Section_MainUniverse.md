---
title: "Launchpad PPA Section: Main/Universe"
date: 2011-04-27
forum: Packaging and Compiling Programs
---

### Post by scott-ian on 2011-04-27
I have created a simple program, and made a deb for it.  I have tried uploading to my new PPA, but I do not know what section to use.  Neither main nor universe work.  What does?

---

### Post by scott-ian on 2011-04-27
Ok, [http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections](http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections) explained that part, but now it is complaining that I have both binary and source.  Can I upload only one?

---

### Post by SevenMachines on 2011-04-28
Yes, you upload source only to launchpad, specify this by using
```
 $ debuild -S
```
on building your package

---

### Post by scott-ian on 2011-04-30
Thanks.  Now it works.

---

