---
title: "Building DEB"
date: 2011-01-31
forum: Packaging and Compiling Programs
---

### Post by Avidanborisov on 2011-01-31
Hello everyone.
in the control file what should i write under architecture?
thanks :)

---

### Post by Rhubarb on 2011-01-31
This is the architecture of the machine than your deb file will happily run on.

If it'll only run on x86 based 64bit computers, then use **amd64**
If it'll only run on x86 based 32bit computers, then use **i386**

And if it can work on all architectures (for example, it's a python app), then use **all**

There are also many other architectures that debian (not so much ubuntu) supports:
**alpha**, **arm**, **armel**, **hppa**, **ia64**, **mips**, **mipsel**, **powerpc**, **s390**, **sparc**

---

### Post by Avidanborisov on 2011-01-31
I think it should work on all.
basicly, it is just a package with some scripts and images...
and can i write this way? - 
architecture: amd64, i386
I mean that it can work on both.

---

### Post by SevenMachines on 2011-01-31
Also note 'any'
> any matches all Debian machine architectures and is the most frequently used. 
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Architecture](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Architecture)

---

### Post by Rhubarb on 2011-01-31
> **Avidanborisov said:**
> ...basicly, it is just a package with some scripts and images...

If it's just some interpreted scripts (such as from python, bash, php), and it contains no compiled code, then use **all** as the architecture type. :)

---

### Post by Avidanborisov on 2011-01-31
OK :)
just a question - 
what happens if I write all but for example amd64 is not supported?
And if I would like to compile a simple program in C - how can I be sure that it will work on amd64?
Can I compile to amd64 when I am using i368?

---

### Post by Avidanborisov on 2011-01-31
Someone?

---

### Post by SevenMachines on 2011-01-31
> **Avidanborisov said:**
> OK :)
just a question - 
what happens if I write all but for example amd64 is not supported?

As mentioned before, at least to the best of my knowledge, 

* 'all' - means its architecture independendent, things like python, java, scripts and the like, you don't specify architecture

* 'any' - means that it's expected to work on all supported architectures, not that it does, but just that theres no reason that it explicitly shouldn't be build on a particular architecture. This is usually what you want. 

* arch list - A case where you might want to explicitly state what architectures to use might be if you have something like inline assembly or something similar with will definitely not work on an archtecture. In which case you specify the supported architecture in a list like i386, powerpc or whatever

> 
And if I would like to compile a simple program in C - how can I be sure that it will work on amd64?It's not meant that you should know if it works on all the supported architectures (theres quite a few, especially on debian). Just that its not specifically barred from working on them.

> Can I compile to amd64 when I am using i368?To an extent, you can cross compile for amd64 on i386, the i386 repositories contain a lot of 'lib64*' packages for i386 to allow this, and of course you could install you're own if needs be. You can also use pbuilder to build on different ubuntu architectures and distributions too.

---

