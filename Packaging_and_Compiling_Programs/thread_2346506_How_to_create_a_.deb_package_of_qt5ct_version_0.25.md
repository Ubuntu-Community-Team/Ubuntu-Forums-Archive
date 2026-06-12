---
title: "How to create a .deb package of qt5ct version 0.25?"
date: 2016-12-15
forum: Packaging and Compiling Programs
---

### Post by &amp;KyT$0P# on 2016-12-15
I'm trying to create a .deb package of qt5ct version 0.25, because of [this]("https://ubuntuforums.org/showthread.php?t=2343084").  Compiling it from source is working, but I'm hitting some roadblocks on packaging it.

1) For other software, the method I've seen for getting all the files is -
```
mkdir debian
DESTDIR=debian make install
```
However, qt5ct seems to ignore the DESTDIR, so the command fails.  How to get it to install to someplace other than / ?  Or is there a better way to go about this step?

2) Build dependencies are usually not the same as runtime dependencies.  So how to get runtime dependencies, for putting in the control file?

The build machine is a disposable Xubuntu 16.04 64-bit VM.  Target platform is also 64-bit Xubuntu 16.04.

Thanks in advance.

---

### Post by &amp;KyT$0P# on 2016-12-28
Did some more intense digging, looks like qt5ct uses [FONT=Courier New]INSTALL_ROOT[/FONT] instead of [FONT=Courier New]DESTDIR[/FONT].  So question #1 is answered.

For question #2, would [FONT=Courier New]ldd[/FONT] help to get the runtime dependencies?  If so, what to do with its output?

---

### Post by &amp;KyT$0P# on 2017-01-23
This looks like a start of an answer - [https://wiki.ubuntu.com/AutoDeb]("https://wiki.ubuntu.com/AutoDeb")

Specifically, the command it uses to get runtime dependencies is [FONT=Courier New]ldd -u [/FONT].  I'll play with that and [FONT=Courier New]apt-file[/FONT] and if it seems to work, will mark this thread as solved.


* Since I already had the runtime dependencies on my system, I was able to use [FONT=Courier New]dpkg-query -S [/FONT] instead of [FONT=Courier New]apt-file[/FONT].  And with that, I think I've successfully created the desired .deb package. :D

---

### Post by &amp;KyT$0P# on 2017-02-13
> **halogen2 said:**
> Specifically, the command it uses to get runtime dependencies is [FONT=Courier New]ldd -u [/FONT].
I've just discovered that does not actually give a complete list of dependencies.

This seems to do better -
```
objdump -p [COLOR="#808080"]<executable or shared library>[/COLOR] | grep NEEDED
```

Then I use the output of [FONT=Courier New]ldconfig -p[/FONT] to find the full paths to the libraries.

---

