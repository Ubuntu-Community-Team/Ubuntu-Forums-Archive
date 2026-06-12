---
title: "Some help compiling Beryl?"
date: 2006-10-26
forum: Packaging and Compiling Programs
---

### Post by Peepsalot on 2006-10-26
I'd like to try my hand at making some patches for Beryl.

I am familiar with c++, but not so much with the ways of Linux program installations from source.  Can anyone help me with this?

So far I've downloaded the full trunk from svn, following the instructions [here](http://bugs.beryl-project.org/)
```
svn co http://svn.beryl-project.org/trunk/
```

There is a directory under the trunk called distro-specific-build-files, which contains some debian specific files for the different components of beryl.  I just don't know what I'm supposed to do with these.

My goal is to be able to edit the code, and then have it build in a way that  replaces my current installation, so I can test my changes.

I'm pretty sure the changes I want to make will all be in the "beryl-plugins" part of the project if that simplifies things.

---

### Post by magicfab on 2006-10-26
I think you'll have better luck posting in beryl-project.org 's forums.

Also see:
[http://wiki.beryl-project.org/index.php/Compile/Sources](http://wiki.beryl-project.org/index.php/Compile/Sources)

---

### Post by Peepsalot on 2006-10-27
Ok, I guess you just run makeall and the distro specific files are handled for you.

It seems to work I think, but something that is confusing me is there are some minimum and maximum limits in the code for the settings sliders, but when running the program these sliders have different min/max limits.

---

