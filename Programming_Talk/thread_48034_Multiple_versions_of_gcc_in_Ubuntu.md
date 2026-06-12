---
title: "Multiple versions of gcc in Ubuntu?"
date: 2005-07-10
forum: Programming Talk
---

### Post by Hikaru79 on 2005-07-10
I'd like to keep two or three different versions of gcc installed, namely gcc-3.3.5, gcc-3.4 and gcc-4.0 . They're all there in apt-get, but I've got some questions about having them all live together in harmony.

In Gentoo, where I got most of my Linux background, there was a neat utility called gcc-config that would allow you to set a system compiler that root would use, and then individual user compilers for each account, which could be easily switched up. This is a perfect solution, but unfortunatly I can't find a similar utility in Ubuntu.

I noticed that by running ls -al on /usr/bin/gcc, it is a symlink to gcc-3.3 . If I were to install gcc-4.0 for example, would it change that symlink? If I wanted to use gcc-4,0 for a particular compilation instead of 3.3, would it be enough to simply use 'gcc-4.0' instead of 'gcc' (which is a symlink to gcc-3.3)? Or are there loads of environment variables (Some distros use $CC, but Ubuntu doesn't seem to) that I also have to set? make.conf files? Anything?

I'd really appreciate an authoratative answer on this. Thanks in advance!!

---

### Post by LordHunter317 on 2005-07-11
[QUOTE=Hikaru79]This is a perfect solution, but unfortunatly I can't find a similar utility in Ubuntu.[/quote]Ubuntu might have made GCC obey the alternatives system, but I don't know if they have for certain.  Debian I know does not.

You could check with update-alternatives --list IIRC.  If GCC is listed, you can use update-alternatives to manage the different versions.

> I noticed that by running ls -al on /usr/bin/gcc, it is a symlink to gcc-3.3 . If I were to install gcc-4.0 for example, would it change that symlink?I don't believe so, but it's dependent on the above.

>  If I wanted to use gcc-4,0 for a particular compilation instead of 3.3, would it be enough to simply use 'gcc-4.0' instead of 'gcc' (which is a symlink to gcc-3.3)?Generally, yes.  You may have to export CC=gcc-4.0 for make.  A very few builds are broken and won't obey environment variables, in which case you'll have to set the symlink (VMware, I'm looking at you).

> (Some distros use $CC, but Ubuntu doesn't seem to)That's a toolchain thing and all distros will use it.

---

