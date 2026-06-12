---
title: "How do I install tar.gz applications?"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-09-19
Hello,
I'm trying to install a tar.gz application. How do I go about compiling it?

---

### Post by skyzthelimit230 on 2011-09-19
I want to install this guy

[http://fold.it/portal/](http://fold.it/portal/)

---

### Post by -kg- on 2011-09-19
[http://ubuntuguide.net/how-to-uncompress-and-install-targztarbz2rar-packages-in-ubuntu]("http://ubuntuguide.net/how-to-uncompress-and-install-targztarbz2rar-packages-in-ubuntu")

---

### Post by garvinrick4 on 2011-09-19
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    [COLOR=Red]./configure[/COLOR] will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    [COLOR=Red]make[/COLOR] will compile all the source files into executable binaries.
    Finally, [COLOR=Red]make install [/COLOR]will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions.[COLOR=Red] Open INSTALL or README file for more information:[/COLOR]

---

### Post by ddnev45 on 2011-09-19
[Looks like you're trying to compile from source.]("http://www.tuxfiles.org/linuxhelp/softinstall.html")

After you unpack the tar.gz file, there should be a README and/or INSTALL text file in the new directory - be sure to read those before compiling.

You'll also have to install the build-essential package from the repos before compiling.

---

### Post by oldos2er on 2011-09-20
This is not source code, it's a precompiled binary. [http://foldit.wikia.com/wiki/FoldIt_Wiki](http://foldit.wikia.com/wiki/FoldIt_Wiki)

---

