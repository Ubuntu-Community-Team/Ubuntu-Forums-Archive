---
title: "compiling webkit nightly on Ubuntu 10.04"
date: 2011-03-27
forum: Packaging and Compiling Programs
---

### Post by otakuj462 on 2011-03-27
Hi,

I'd like to compile a Webkit nightly on Ubuntu 10.04, but it looks like the version of glibc included with 10.04 is too old (2.10, whereas 2.27.90 is needed by upstream Webkit). What's the easiest way to get set up to compile a Webkit nightly on Ubuntu 10.04? I'd like to be able to compile it myself, rather than just downloading binaries from a ppa, as there are a few bugs I've found which I'd like to try fixing myself.

I'd appreciate any guidance anyone can provide. Thanks,

Jake

---

### Post by MadCow108 on 2011-03-27
> **otakuj462 said:**
> Hi,
... (2.10, whereas 2.27.90 is needed by upstream Webkit)

wow thats some software from the future :O
current libc version is 2.13

you sure libc is the problem? not much has changed since 2.10

is there a nightly ppa for 10.04?
if yes just download the source of that ppa with apt-get source ...
that source must compile in 10.04 (maybe with some patches usually located in debian/patches).

---

### Post by otakuj462 on 2011-03-27
> **MadCow108 said:**
> wow thats some software from the future :O

Here's the error I'm getting when building:


```
checking for GLIB - version >= 2.27.90... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: You need the GLib dev tools in your path

```

Doesn't that mean it wants a glibc version above 2.27.90?

I'll look into your ppa suggestion as well. Thanks,

Jake

---

### Post by MadCow108 on 2011-03-27
glib is not glibc.
glibc is the gnu c library.
glib is the gnome support library, 10.04 has version 2.26 of that.

there is a ppa with 2.28 here:
[https://launchpad.net/~kalon33/+archive/experimental-stuff/+packages?start=75&batch=75](https://launchpad.net/~kalon33/+archive/experimental-stuff/+packages?start=75&batch=75)
but as  glib is an important component of gnome using it could break your system.
Better not use your main installation for this.
(you could also install 11.04 alpha for testing, it also has 2.28)

---

### Post by otakuj462 on 2011-03-27
> **MadCow108 said:**
> glib is not glibc.
glibc is the gnu c library.
glib is the gnome support library, 10.04 has version 2.26 of that.

there is a ppa with 2.28 here:
[https://launchpad.net/~kalon33/+archive/experimental-stuff/+packages?start=75&batch=75](https://launchpad.net/~kalon33/+archive/experimental-stuff/+packages?start=75&batch=75)
but as  glib is an important component of gnome using it could break your system.
Better not use your main installation for this.
(you could also install 11.04 alpha for testing, it also has 2.28)

Thanks, I'll probably go the route of installing 11.04.

---

