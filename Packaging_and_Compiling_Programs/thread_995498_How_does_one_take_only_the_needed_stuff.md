---
title: "How does one take only the needed stuff?"
date: 2008-11-27
forum: Packaging and Compiling Programs
---

### Post by mickbuntu on 2008-11-27
hello,

After compiling a program, one has junk in the build dir. How does one only extract the needed stuff to be packaged? Otherwise the deb-creator will package even the source code. Thanks.

---

### Post by hissyfut on 2008-11-28
What is deb-creator?

The answer to your question depends on how you have built the program at this point. If you have only compiled the source with no deb package commands or with no debian directory, then it depends on if the program uses the autoconf way or a simple makefile way. If the program uses the autoconf way - (configure make make install), then you "MIGHT" be able to install into a temporary directory where you can then make a deb package.
In the source directory, try a "grep -ir destdir *". If you see a bunch of destdir listings, then "most likely" the program will install properly into a temporary directory by doing a "make DESTDIR=/some/path install".

---

### Post by mickbuntu on 2008-11-29
Hello,

> **hissyfut said:**
> What is deb-creator?

The answer to your question depends on how you have built the program at this point. If you have only compiled the source with no deb package commands or with no debian directory, then it depends on if the program uses the autoconf way or a simple makefile way. If the program uses the autoconf way - (configure make make install), then you "MIGHT" be able to install into a temporary directory where you can then make a deb package.
In the source directory, try a "grep -ir destdir *". If you see a bunch of destdir listings, then "most likely" the program will install properly into a temporary directory by doing a "make DESTDIR=/some/path install".

This is what I was trying to do first from another thread: It works well, but one also would package unneeded files. Thanks though for reply.



> **Arlanthir said:**
> I'm no PRO, but I'll give it a shot!

Create a folder on your home called *PACKAGENAME*.
Inside, you're going to have 2 folders: *DEBIAN* and *usr*.

On *usr*, you recreate the files and folders you want your file system to have after install.
Meaning, if you want to have an application in /usr/share/myprogram
you would create a folder named *share* in *usr* and then another named *myprogram* in *share*. Something like this:

/home/you/PACKAGENAME
[INDENT]|
       |--- DEBIAN
       |--- usr
[INDENT]|
        |--- share
[INDENT]       |
               |--- myprogram
[/INDENT][/INDENT][/INDENT]


That's it for the data files. On to the DEBIAN folder.
The DEBIAN folder is used to provide package information.

Inside, it will only have a single textfile named *control*

Here is a template *control* file for you to work on:

```

Package: myprogram
Priority: optional
Section: games
Installed-Size: 91.3
Maintainer: L0tU5
Architecture: i386
Version: 0:0.5
Depends: libgtk2.0-0, python-gtk2
Description: A super program.

```


After all that, you're ready to build the package!
Fire up a terminal and issue the following command:

```

dpkg-deb -b PACKAGENAME

```

So, there you go, I hope I was clear =)
I think it's slightly handcrafted and there are probably more automatic ways, but this is the only one I know :P

**Notes:** Don't forget to change PACKAGENAME and myprogram to names of your choosing! About the menu entries, you'll have to create the .desktop files you want and place them in /usr/share/applications. Check that folder for some examples (open them with gedit!)

---

### Post by InfinityCircuit on 2008-11-29
It is impossible to support Debian packaging using a DEBIAN binary control file.

See [http://ubuntuforums.org/showthread.php?t=958456](http://ubuntuforums.org/showthread.php?t=958456) for a more complete discussion of the problems and suggestions on better approaches to package management.

---

### Post by danf_1979 on 2008-11-30
$ debuild clean
$ debuild -S

---

### Post by hissyfut on 2008-12-01
> **InfinityCircuit said:**
> It is impossible to support Debian packaging using a DEBIAN binary control file.

It seems to work fine, just as Arlanthir stated. Have used this and it works easy, all you need is keep a template of control file and copy it into a DEBIAN directory of the root install directory.
For example:

mkdir /var/tmp/program-1.1

# this might better done with sudo then files will have
# appropriate ownership. In fact this part might better done
# through fakeroot, but not familiar with it yet.
make DESTDIR=/var/tmp/program-1.1 install
mkdir /var/tmp/program-1.1/DEBIAN
cp /path/to/control /var/tmp/program-1.1/DEBIAN/

# edit control to fit program-1.1

cd /var/tmp
dpkg-deb --build program-1.1

This is only for a private install and not for a package uploaded to a community.

---

