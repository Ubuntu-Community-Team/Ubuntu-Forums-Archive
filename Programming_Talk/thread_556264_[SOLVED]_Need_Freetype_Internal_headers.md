---
title: "[SOLVED] Need Freetype Internal headers"
date: 2007-09-21
forum: Programming Talk
---

### Post by dwhitney67 on 2007-09-21
I'm trying to build qt-x11-free-3.2.3 on an Ubuntu 7.04 system.  I am getting the following compile errors:

[FONT="Courier New"]3rdparty/opentype/ftxopen.c:18:40: error: freetype/internal/ftstream.h: No such file or directory
3rdparty/opentype/ftxopen.c:19:40: error: freetype/internal/ftmemory.h: No such file or directory
3rdparty/opentype/ftxopen.c:20:39: error: freetype/internal/tttypes.h: No such file or directory[/FONT]

Does anybody know where I can "apt-get" the internal header files for Freetype?  I've searched the web and have found nothing.  These files are available on my Fedora Core 5 system.

Are the files I am looking for obsolete (i.e. unavailable with the latest version of Freetype)?

---

### Post by tr333 on 2007-09-21
"apt-cache search freetype" came up with the following results:

libfreetype6
libfreetype6-dev

Try installing those packages.

---

### Post by dwhitney67 on 2007-09-21
Thanks, but I have already tried that.  Apparently I already have those packages installed.  I am starting to believe that perhaps the curators of Freetype have decided to deep-six the "internal" directory along with the header files within such.

I think it is time to remove the Ubuntu 7.04 installation so that I can install an older version of Linux, thus enabling me to build an "ancient" software package such as Qt 3.2.3.

If anyone else has any suggestions, by all means they are welcome.  I have a wonderful employer who provides me the luxury to experiment with new build procedures, operating systems, and platforms, all at my discretion.

---

### Post by dwhitney67 on 2007-09-21
I just noticed something different between two Ubuntu systems I have.  One, which perhaps a month or two ago, when I installed "xorg-dev", the "libfreetype6-dev" was _not_ installed as a dependency.

With a system I setup yesterday, it is being included as a dependency.

Is there a way to install "xorg-dev", but selectively exclude other package(s) I do not want?

---

### Post by tr333 on 2007-09-22
"xorg-dev" is just a metapackage - a package that only depends on other packages, and doesn't contain any stuff itself.  Think of it as a group of packages.

"apt-cache show xorg-dev" will list all of the dependencies of the "xorg-dev" package, allowing you to pick and choose the packages you want to install.

---

### Post by dwhitney67 on 2007-09-22
Thanks for the info.  I will keep it mind.  For now I decided to blow away the Ubuntu installation and install Fedora Core 4 in its place.  Because FC4 provides an older version of Freetype, I think Qt-3.2.3 will be "happier" when I build it.

If later I decide not to use FC4 and return to Ubuntu 7.04, then I will configure Qt-3.2.3 to not include the Freetype features.

---

### Post by geraldm on 2007-09-22
"internal/" is in freetype2 package, not freetype package.

Gerald

---

### Post by dwhitney67 on 2007-09-22
Here's the listing of the /usr/include/freetype2/freetype/internal directory under my Fedora Core 4 system:

[PHP]user@olympic:/usr/include/freetype2/freetype/internal] 
> lx
autohint.h  ftgloadr.h  ftserv.h    pcftypes.h  svbdf.h     svpostnm.h  svttcmap.h  tttypes.h
ftcalc.h    ftmemory.h  ftstream.h  psaux.h     svgldict.h  svpscmap.h  svwinfnt.h
ftdebug.h   ftobjs.h    fttrace.h   pshints.h   svmm.h      svpsinfo.h  svxf86nm.h
ftdriver.h  ftrfork.h   internal.h  sfnt.h      svpfr.h     svsfnt.h    t1types.h[/PHP]

My Ubuntu 7.04 system did not have an "internal" directory under /usr/include/freetype2/freetype, thus I was unable to build Qt-3.2.3.

Please tell me that I am wrong and that there is a way to obtain the files available with the FC4 distro.  Is the "complete" freetype2 package available?  If so, what is the package name and what repo it is in?

---

### Post by geraldm on 2007-09-23
[http://sourceforge.net/project/showfiles.php?group_id=3157](http://sourceforge.net/project/showfiles.php?group_id=3157)

If the last character ] is also in the directory name, remove it.

Gerald

---

### Post by tr333 on 2007-09-24
There seems to be a [bug report](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/72635) on this issue, but it's almost a year old :(
Is there any way to get this bug looked at more closely?

---

### Post by geraldm on 2007-09-25
tr333,

I have updated the bug report with a note on the API changes
that were made 2006-05-13, which refer any developer to some
possible patches for correction to their source. 

Gerald

---

### Post by tr333 on 2007-09-25
> **geraldm said:**
> tr333,

I have updated the bug report with a note on the API changes
that were made 2006-05-13, which refer any developer to some
possible patches for correction to their source. 

Gerald

Great! Looks like it wasn't a problem with freetype.

---

### Post by dwhitney67 on 2007-09-25
geraldm -

Thanks for following up on the issue I encountered concerning freetype2.  It appears that there is not much I can do other than uninstall the latest version of freetype2, and then install an older version that provides the "internal" header files sought by Qt-3.2.3.

It's pretty lame that Trolltech elected to use internal header files for their earlier versions of Qt.  They probably corrected their mistake with their releases after Qt-3.3.5.

Unfortunately I am stuck with using Qt-3.2.3.  I suppose I could experiment with the Qt patch (available through the link in your bug report), however I will have to save that for another day.

For now, I have taken the path of least resistance... I overwrote the installation of Ubuntu 7.04 with Fedora Core 5.  :)

P.S.  Since this thread has met its end, I will close it out.

---

### Post by macetw on 2007-10-08
The other solution is to configure QT 3.2.3 with the -no-xft option, and it won't use the freetype includes/libraries.

-"ancient" QT3.2.1 user who found the same thing.

---

