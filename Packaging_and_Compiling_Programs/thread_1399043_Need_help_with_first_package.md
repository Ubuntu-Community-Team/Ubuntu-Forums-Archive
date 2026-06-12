---
title: "Need help with first package"
date: 2010-02-05
forum: Packaging and Compiling Programs
---

### Post by agnes on 2010-02-05
I'm trying to make a Karmic amd64 package (with dh-make) for PLT Scheme.

Now I have some simple questions which aren't in the Debian tutorial:

1. What is an upstream author? I mean, what should I put in the following sections in /debian/copyright.txt:
```
Upstream Author(s):

    <put author's name and email here>
    <likewise for another author>

Copyright:

    <Copyright (C) YYYY Name OfAuthor>
    <likewise for another author>
```

2. The debian directory is not in the same directory as where the configure-, make- and makefile-scripts are. The directory structure is as follows:
```

----> /plt-package
   |
   |-----> /debian
   |
   |-----> /src
       |
       |-----> configure, make, make install

```

I guess this means I need to edit some settings in /debian/rules. (How) should I account for this?

Thanks in advance.

---

### Post by SevenMachines on 2010-02-06
hi.
1. upstream author is essentially the person/persons or company that wrote the software. see [debian copyright policy.]("http://www.debian.org/doc/debian-policy/ch-docs.html#s-copyrightfile")
especially " the copyright file must say where the upstream sources (if any) were obtained.  It should name the original authors of the package and  the Debian maintainer(s) who were involved with its creation."
you are the debian maintainer in that sentence :)
The authors and who holds the copyright should be included with the source code, if not, you'll need to check with the people at source codes home to see what is needed 
if plt has a simple open source license then there shouldnt be any problem. packaging the copyright file is essential and so every package installed will have a file /usr/share/doc/<packagename>/copyright installed if your looking for examples

2. this really depends on how you've written your debian/rules file. i'm not sure if theres a way to pass variables to cdbs to deal with this simply. but if you are using your own build: rules and so on it shouldnt be too difficult (fingers crossed :) )

hope that was at least a little helpful, good luck!

---

### Post by Bachstelze on 2010-02-06
Do you want to create your package using the same, strict rules that need to be obeyed by official packages, or do you /care and just want to create the package for yourself? If you want to go with the former, there are a lot of things that must be taken into account (for starters, the upstream tarball should *not* contain a debian/ directory).

---

### Post by agnes on 2010-02-06
Well this first package I just wanted to compile "for myself" to learn something from it. Maybe make available on the internet.
But probably later I will want to make official packages, so do you know where the rules for that are listed?

Anyway, thanks SevenMachines. Also, I've configured the 'rules' file so it worked, was not really hard. (see attachments)

It still doesn't compile though,  but that's probably because for another reason.
(By compiling I mean running **dpkg-buildpackage -rfakeroot**)
At first it was busy compiling for a while but then there was some dependency error in some of the libraries this package needs... so it quit.
Then I tried it again but even after recopying the original /src dir it says
```
dpkg-source: error: cannot represent change to plt-4.2.4/src/mred/libmred3m.a: binary file contents changed
dpkg-source: error: cannot represent change to plt-4.2.4/src/mzscheme/starter: binary file contents changed
dpkg-source: error: cannot represent change to plt-4.2.4/src/mzscheme/mzschemecgc: binary file contents changed
dpkg-source: warning: executable mode 0755 of 'src/foreign/gcc/libffi/libtool' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'src/foreign/gcc/libffi/config.status' will not be represented in diff
dpkg-source: error: cannot represent change to plt-4.2.4/src/foreign/gcc/libffi/include/ffitarget.h:
dpkg-source: error:   new version is symlink to .././src/x86/ffitarget.h
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: newly created empty file 'src/foreign/gcc/libffi/src/.dirstamp' will not be represented in diff
dpkg-source: warning: newly created empty file 'src/foreign/gcc/libffi/src/.deps/.dirstamp' will not be represented in diff
dpkg-source: warning: newly created empty file 'src/foreign/gcc/libffi/src/x86/.dirstamp' will not be represented in diff
dpkg-source: warning: newly created empty file 'src/foreign/gcc/libffi/src/x86/.deps/.dirstamp' will not be represented in diff
dpkg-source: warning: ignoring deletion of file src/mzscheme/gc/libatomic_ops/src/atomic_ops/sysdeps/gcc/x86.h.orig
dpkg-source: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b plt-4.2.4 gave error exit status 1
```

I will try it all over again later, report results.

---

### Post by Bachstelze on 2010-02-06
You might want to start with a simpler package. The [Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide") is a good place to start, it should give you a fair idea of the Do's and Dont's. Also you can step by #ubunntu-motu on IRC if you have questions, people will be happy to help you. I think they are also holding periodic packaging training sessions.

---

### Post by agnes on 2010-02-06
Thanks, and I guess it's indeed a better idea to start with something simpler.

---

