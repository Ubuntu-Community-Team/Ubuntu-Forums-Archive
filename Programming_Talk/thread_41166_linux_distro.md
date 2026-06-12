---
title: "linux distro"
date: 2005-06-12
forum: Programming Talk
---

### Post by joshlink01 on 2005-06-12
I wanted to create my own Linux Distro but I found it to complicated. (I used LFS). So, I read some where that some Linux Distro (never herd of it) was just a heavily modified popular distro. Could I do that? And how could I change the boot screen ect. so I could do that.

---

### Post by crane on 2005-06-12
[QUOTE=joshlink01]I wanted to create my own Linux Distro but I found it to complicated. (I used LFS). So, I read some where that some Linux Distro (never herd of it) was just a heavily modified popular distro. Could I do that? And how could I change the boot screen ect. so I could do that.[/QUOTE]


Not quite sure what you mean. A lot of the most popular distros are built from Redhat, Debian, Slack, and Gentoo. Even Ubuntu is based on debian.
 There are a few programs that allow you to build your own. I think the latest version of Knoppix allows this.
 Are you wanting to build a custum install/Live CD for youself? Or are you talking about building one to release? If you build one to release then I suggest you learn linux and you version inside and out. People will try it and have many many questions and problems.

---

### Post by skoal on 2005-06-12
An LFS'er? sweet!  It's always good to run across an old LFS buddy.  To answer your question, a distro is pretty much just a collection of packages wrapped in a specific package manager format, an installer, and a few scripts to wrap up the lose ends and get things rolling.  The Ubuntu developers are probably falling outta their chairs laughing at me right now, and I am oversimplifying it a bit.

However, download the anaconda source from a redhat site.  I unpacked that (sweet) installer some time ago for my own distro project, and you'll get a good idea of what's needed (for that part of a distro CD at least).  All the source is in python, with a few C hooks.  Since you're an LFS'er, I don't need to tell you that the only other major task is to compile the tool chain, kernel, apps, etc., all within a chroot (as one example).  Slap those compiled packages into an ISO, throw your own unique "bastardized" anaconda installer in there, and make the ISO CD bootable.  There ya go...THe JoshLinkus distro CD, v1.0.

\\//_

---

### Post by joshlink01 on 2005-06-12
[QUOTE=skoal]An LFS'er? sweet!  It's always good to run across an old LFS buddy.  To answer your question, a distro is pretty much just a collection of packages wrapped in a specific package manager format, an installer, and a few scripts to wrap up the lose ends and get things rolling.  The Ubuntu developers are probably falling outta their chairs laughing at me right now, and I am oversimplifying it a bit.

However, download the anaconda source from a redhat site.  I unpacked that (sweet) installer some time ago for my own distro project, and you'll get a good idea of what's needed (for that part of a distro CD at least).  All the source is in python, with a few C hooks.  Since you're an LFS'er, I don't need to tell you that the only other major task is to compile the tool chain, kernel, apps, etc., all within a chroot (as one example).  Slap those compiled packages into an ISO, throw your own unique "bastardized" anaconda installer in there, and make the ISO CD bootable.  There ya go...THe JoshLinkus distro CD, v1.0.

\\//_[/QUOTE]
Woah! Sounds too confusing for me but I'll try it.

---

