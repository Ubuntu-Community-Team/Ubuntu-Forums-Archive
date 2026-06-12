---
title: "Alas, I cannot click, and stuck with tar files"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Skyvaal Valun on 2011-10-23
I have recently used Wubi to install Ubuntu onto my desktop, having also used it to get it on my Netbook. On my netbook, there are no problems with input devices and the touchscreen works perfectly, meaning I can browse around without hindrance.
However, moving to my super-awesome desktop, I find that it doesn't use my mouse correctly.
All it lets me do, is to open a program from the sidebar by clicking it, then it tuirns around and goes "Hmm.. You know what, I don't want to let you click anything else now."
The mouse I use is a Saitek Cyborg R.A.T 5, and I've tried with my Kensington Rollerball too, still no change...
At the moment, my primary concern is that I will not be able to navigate my folders easily without this, but I do have a second, slightly more trivial question too.

On my netbook (which has straight up ubuntu, not ubuntu netbook), I require several files for the University course I'm on, however, I have the tar.gz files, and don't know where to proceed from there. I asked my lecturer to tell me, but he simply installed the first file for me, and since then, I cannot actually figure out how to do it myself...
Obviously, this will be second nature to some of you, so if you could tell me what I'd need to type into terminal, I'd be VERY grateful.

---

### Post by MG&amp;TL on 2011-10-23
Detar a .tar.gz:


```
cd <directory containing tarball>
tar -zcvf <archive_name.tar.gz directory_to_compress>
```

Or open it with archive manager on your laptop, by right clicking, open with > archiuve manager.

---

### Post by garvinrick4 on 2011-10-23
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

    ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

---

