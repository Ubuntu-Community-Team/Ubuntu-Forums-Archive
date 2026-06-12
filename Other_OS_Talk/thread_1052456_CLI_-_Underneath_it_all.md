---
title: "CLI - Underneath it all"
date: 2009-01-27
forum: Other OS Talk
---

### Post by transmition on 2009-01-27
I have a question. When working with a pure CLI system, what are the differences between linux distributions. The only two things that come to mind are:

-sudo and su
-package management

Anything else?

---

### Post by diwas on 2009-01-27
Yes, I guess the syntax of some commands are different. I am not sure though.

---

### Post by cardinals_fan on 2009-01-27
Different init systems are also worth mentioning.

EDIT: Different distros also have different policies on patching and/or modifying packages.  This can affect the security and functionality of the software in the repos.

---

### Post by RedSquirrel on 2009-01-27
The default configuration files (and relevant directories) under /etc can vary quite a bit (both in existence and content). The init configuration is one example, but there are many others, of course (/etc/profile, application defaults, e.g., for vim...).

On a user level, configuration files (e.g., copied from /etc/skel) can be quite different from distro to distro. The default ~/.bashrc can be nearly empty or even nonexistent.

You can also see different amounts of software installed by default (Hey! Where's **less**?!), and different versions with potentially different levels of functionality (read those man pages! :)).

---

### Post by transmition on 2009-01-27
> **RedSquirrel said:**
> The default configuration files (and relevant directories) under /etc can vary quite a bit (both in existence and content). The init configuration is one example, but there are many others, of course (/etc/profile, application defaults, e.g., for vim...).

On a user level, configuration files (e.g., copied from /etc/skel) can be quite different from distro to distro. The default ~/.bashrc can be nearly empty or even nonexistent.

You can also see different amounts of software installed by default (Hey! Where's **less**?!), and different versions with potentially different levels of functionality (read those man pages! :)).

Thanks, that is exactly the type of response I was looking for (and if the thanks button would show up I would thank you)

---

### Post by Sorivenul on 2009-01-27
You're also looking at default hardware support (so kernel) variations between the distributions. A CLI install of Ubuntu on my laptop works differently than the CLI install of Debian, even though they are "related", because of Debian's philosophy regarding non-free software. Outside of that, it has been covered by the other fine folks here. :D

---

### Post by wolfen69 on 2009-01-27
if you want to learn command line and still have fun, check out [INX]("http://inx.maincontent.net/announce-inx-1.0.html"). it's total command line goodness. it has built in tutorials too. very nice.

---

### Post by Noour on 2009-01-27
There are differences between distros but also lots of similarities
A good link regarding CLI basics : [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Debian and Ubuntu have lots of similarities [Similar popular packages => similar principles => not so big differences inside configuration files]. 

Programming languages used in the recent distros tend also to be the same (g++, something for KDE, something for Gnome, QT3, ... etc etc).

I love Linux CLI oriented operating systems :D

---

### Post by cardinals_fan on 2009-01-27
> **Noour said:**
> 
Programming languages used in the recent distros tend also to be the same (g++, something for KDE, something for Gnome, QT3, ... etc etc).

Just to quibble, you're referring to major compilers and toolkits, not programming *languages* per se.

The init systems really do make quite a difference.  The two most common are System V style and BSD style, but I really like the [SliTaz system]("http://www.slitaz.org/en/doc/cookbook/boot-scripts.html"): no runlevels!  I believe Gentoo has their own as well (can't remember for sure).  Ubuntu uses Upstart, which is intentionally similar to System V for backwards-compatibility.

[http://en.wikipedia.org/wiki/Init](http://en.wikipedia.org/wiki/Init)

---

### Post by fistfullofroses on 2009-01-28
Package selection, base package choice (busybox vs coreutils/binutils), networking packages (netkit vs others), alsa yes/no, there are more differences in CLI systems than graphic systems really, because each difference can add or subtract functionality at a very basic level. Also think about the fact that you will have to memorize commands, and the options for different programs can be very confusing, as well as syntax differences. You also need to think of what the shell is bash, zsh, ash, korn, tcsh, etc...

---

### Post by saulgoode on 2009-01-28
One distinction that is relatively minor in nature but which can be disorienting is that there are different degrees of "tab completion" provided by various distros. Some distros offer context sensitive tab completion which will, for example, only display subdirectories if a 'cd' command is being executed -- or if the 'man' command is being performed, will list potential pages available (ignoring directory and files altogether). Other distros use bare-bones tab completion based only on the file and subdirectory names available.

---

### Post by cardinals_fan on 2009-01-28
> **saulgoode said:**
> One distinction that is relatively minor in nature but which can be disorienting is that there are different degrees of "tab completion" provided by various distros. Some distros offer context sensitive tab completion which will, for example, only display subdirectories if a 'cd' command is being executed -- or if the 'man' command is being performed, will list potential pages available (ignoring directory and files altogether). Other distros use bare-bones tab completion based only on the file and subdirectory names available.
This should only depend on a) the shell used by default and b) the default shell configuration, right?

---

### Post by Sorivenul on 2009-01-28
> **cardinals_fan said:**
> This should only depend on a) the shell used by default and b) the default shell configuration, right?
Correct.

---

### Post by saulgoode on 2009-01-29
> **cardinals_fan said:**
> This should only depend on a) the shell used by default and b) the default shell configuration, right?
BASH programmable completion is a separate package from BASH and may or may not be included with a distro. This is a distinction just as other package choices are, whether Init alternatives, SUDO, or the various shell interpreters.

---

### Post by MisfitI38 on 2009-01-30
..the absence or presence of a ports system.

---

