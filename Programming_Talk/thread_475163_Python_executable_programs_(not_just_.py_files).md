---
title: "Python executable programs (not just .py files)"
date: 2007-06-15
forum: Programming Talk
---

### Post by SnakeByte29 on 2007-06-15
Is there a way to create executables with python on linux? I've used py2exe on windows and I'm looking for something similar. I've heard of something called "freeze.py" that supposedly does this but I can't find it anywhere on my system.

---

### Post by Bachstelze on 2007-06-15
You can execute Python scripts directly. Just put that in the first line of your script :

```
#!/usr/bin/env python
```

Make the file executable with

```
chmod +x file.py
```

and you can execute it with

```
./file.py
```

---

### Post by SnakeByte29 on 2007-06-15
I know you can execute .py files, but what I'd really like is something that creates a new file that would be executable rather than just a regular python file. Is that possible?

---

### Post by pmasiar on 2007-06-15
how it is different? You have file and it is executable (on every system where devendencies are installed).

You may want to look at distutils and egg python package format

---

### Post by avik on 2007-06-15
I'm pretty sure what py2exe does is bundle the python interpreter with the script.  However, on most GNU/Linux systems, either python is already installed or can be easily installed, so there's no problem with just distributing the .py file.  All the major GNU/LInux distributions should include python, and I know for a fact that Ubuntu does.

---

### Post by WW on 2007-06-15
> **pmasiar said:**
> how it is different? You have file and it is executable (on every system where devendencies are installed).


From [py2exe.org]("http://www.py2exe.org/"):  "py2exe is a Python Distutils extension which converts Python scripts into executable Windows programs, able to run *without requiring a Python installation*" (emphasis mine).

---

### Post by loell on 2007-06-15
but would you rather want to bundle a set of python scripts as a deb package , as opposed to py2exe style
or its mythical equilvalent py2bin?

---

### Post by pmasiar on 2007-06-15
> **WW said:**
>  able to run *without requiring a Python installation*" (emphasis mine).

Yes, it avoids installing Python on windows - but if Linux has already Python installed anyway, *what real user need* your packing would solve?

Open source provides different solutions for similar problems. Proprietary systems are working hard around fact that sources and development environments are not free and widely available. But it they *are* free and *are* widely available, why waste time developing solution like in proprietary world?

So on Linux distro, where Python is already installed: how your py2bin solution would be different from just providing sources? BTW  you are still required to provide sources according to GPL.

---

### Post by loell on 2007-06-15
heh, you've missinterpreted me there ;) , py2bin does not offer a solution. it seem it doesn't even exist.
hence i said mythical. 

deb/rpm binary packages is the way to go, that's just my point, also there are distributions that do not bundle python by default.
since it would auto-depend in python , it will auto-diownload python if its not installed.

oh and on a side note, if i declare my script on a commercial license, i am not oblige to provide sources to  the script.

---

### Post by ghostdog74 on 2007-06-16
> **SnakeByte29 said:**
> Is there a way to create executables with python on linux? 

[pyinstaller]("http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi")

---

### Post by johnconnor on 2008-04-27
Hi everyone!

This topic is a bit old but, can I use Py2exe under Ubuntu? I would like to make a tiny Python script Windows users can run without having to install Python. Is Py2exe working just under Windows, or is it possible to generate a .exe file on my system too?

---

### Post by LaRoza on 2008-04-27
> **johnconnor said:**
> Hi everyone!

This topic is a bit old but, can I use Py2exe under Ubuntu? I would like to make a tiny Python script Windows users can run without having to install Python. Is Py2exe working just under Windows, or is it possible to generate a .exe file on my system too?

"A tiny python script" with py2exe? It will be anything but tiny if you do that.

If they are using an HP or Compaq, they likely have Python installed. If they don't, tell them to install the ActivePython version. It is an easy install process.

---

### Post by pmasiar on 2008-04-27
py2exe will create executable binary including all the libraries your code uses, that's why it will NOT be tiny.

IMHO it is simpler for you to persuade your Windows user to download and run single standard ActiveState Python installer than for you monkey around compiler - and you will have to compile py2exe on windows, not on Linux.

---

### Post by WitchCraft on 2008-04-27
> **SnakeByte29 said:**
> Is there a way to create executables with python on linux? I've used py2exe on windows and I'm looking for something similar. I've heard of something called "freeze.py" that supposedly does this but I can't find it anywhere on my system.


I had the same problem. freeze.py is somewhere in (if i remember right /usr/libs or something.

But you need to install python examples first.

Here is how to solve your problem:

apt-file search freeze:
```

root@all:~# apt-file search freeze
asterisk-prompt-es: /usr/share/asterisk/sounds/es/freeze.gsm
asterisk-sounds-extra: /usr/share/asterisk/sounds/freeze.gsm
atheme-services: /usr/lib/atheme/modules/nickserv/freeze.so
atheme-services: /usr/share/atheme/help/nickserv/freeze
atheme-services: /usr/share/atheme/help/userserv/freeze
autoconf-archive: /usr/share/autoconf-archive/ac_cxx_have_freeze_sstream.m4
autoconf-archive: /usr/share/doc/autoconf-archive/html/ac_cxx_have_freeze_sstream.html
cryopid: /usr/bin/freeze
cryopid: /usr/share/man/man1/freeze.1.gz
debian-installer: /usr/share/doc/debian-installer/i18n/en/translators/string-freezes.xml
enigma-data: /usr/share/games/enigma/levels/lib/andreas_itemfreeze.xml
etw-data: /usr/share/games/etw/snd/freeze.wav
freeze: /usr/share/doc/freeze/README
freeze: /usr/share/doc/freeze/changelog.Debian.gz
freeze: /usr/share/doc/freeze/copyright
geomview: /usr/share/doc/geomview/html/freeze.html
geomview: /usr/share/doc/geomview/html/pt_BR/freeze.html
geomview: /usr/share/doc/geomview/html/pt_BR/ui_002dfreeze.html
geomview: /usr/share/doc/geomview/html/ui_002dfreeze.html
gosa: /usr/share/gosa/html/images/.svn/prop-base/freeze.png.svn-base
gosa: /usr/share/gosa/html/images/.svn/prop-base/freeze_grey.png.svn-base
gosa: /usr/share/gosa/html/images/.svn/text-base/freeze.png.svn-base
gosa: /usr/share/gosa/html/images/.svn/text-base/freeze_grey.png.svn-base
gosa: /usr/share/gosa/html/images/freeze.png
gosa: /usr/share/gosa/html/images/freeze_grey.png
gstreamer0.10-plugins-bad: /usr/lib/gstreamer-0.10/libgstfreeze.so
gstreamer0.10-plugins-bad-dbg: /usr/lib/debug/usr/lib/gstreamer-0.10/libgstfreeze.so
gstreamer0.10-plugins-bad-doc: /usr/share/gtk-doc/html/gst-plugins-bad-plugins-0.10/gst-plugins-bad-plugins-plugin-freeze.html
gtk-gnutella: /usr/share/gtk-gnutella/pixmaps/freeze.xpm
hannah-data: /usr/share/games/hannah/freeze/default/clock.png
hannah-data: /usr/share/games/hannah/freeze/default/sprite.dat
horae: /usr/share/perl5/Ifeffit/lib/athena.doc/athena_freeze.pod
jython: /usr/share/jython/Tools/freeze/FreezeVisitor.py
jython: /usr/share/jython/Tools/freeze/Freezer.py
jython: /usr/share/jython/Tools/freeze/Output.py
jython: /usr/share/jython/Tools/freeze/freeze.py
kdenlive-data: /usr/share/apps/kdenlive/effects/freeze.xml
komi: /usr/share/games/komi/sounds_freeze.wav
komi: /usr/share/games/komi/sounds_unfreezewarning.wav
lbreakout2-data: /usr/share/games/lbreakout2/sounds/freeze.wav
liballegro-doc: /usr/share/man/man3/freeze_mouse_flag.3alleg.gz
libcgi-session-perl: /usr/share/man/man3/CGI::Session::Serialize::freezethaw.3pm.gz
libcgi-session-perl: /usr/share/perl5/CGI/Session/Serialize/freezethaw.pm
libdata-serializer-perl: /usr/share/perl5/auto/Data/Serializer/freeze.al
libfreeze32: /usr/share/doc/libfreeze32/README
libfreeze32: /usr/share/doc/libfreeze32/changelog.Debian.gz
libfreeze32: /usr/share/doc/libfreeze32/copyright
libfreezethaw-perl: /usr/share/doc/libfreezethaw-perl/README
libfreezethaw-perl: /usr/share/doc/libfreezethaw-perl/changelog.Debian.gz
libfreezethaw-perl: /usr/share/doc/libfreezethaw-perl/changelog.gz
libfreezethaw-perl: /usr/share/doc/libfreezethaw-perl/copyright
libparrot-dev: /usr/include/parrot/pmc_freeze.h
libqcad0-dev: /usr/include/rs_actionblocksfreezeall.h
libqcad0-dev: /usr/include/rs_actionlayersfreezeall.h
linux-doc-2.6.24: /usr/share/doc/linux-doc-2.6.24/Documentation/video4linux/bttv/README.freeze
linux-headers-2.6.24-16: /usr/src/linux-headers-2.6.24-16/include/linux/freezer.h
linux-headers-2.6.24-16-386: /usr/src/linux-headers-2.6.24-16-386/include/linux/freezer.h
linux-headers-2.6.24-16-generic: /usr/src/linux-headers-2.6.24-16-generic/include/linux/freezer.h
linux-headers-2.6.24-16-openvz: /usr/src/linux-headers-2.6.24-16-openvz/include/linux/freezer.h
linux-headers-2.6.24-16-rt: /usr/src/linux-headers-2.6.24-16-rt/include/linux/freezer.h
linux-headers-2.6.24-16-server: /usr/src/linux-headers-2.6.24-16-server/include/linux/freezer.h
linux-headers-2.6.24-16-virtual: /usr/src/linux-headers-2.6.24-16-virtual/include/linux/freezer.h
linux-headers-2.6.24-16-xen: /usr/src/linux-headers-2.6.24-16-xen/include/linux/freezer.h
lmms-common: /usr/share/lmms/themes/blue_scene/freeze.png
lmms-common: /usr/share/lmms/themes/blue_scene/unfreeze.png
lmms-common: /usr/share/lmms/themes/default/freeze.png
lmms-common: /usr/share/lmms/themes/default/unfreeze.png
manpages-ja: /usr/share/man/ja/man1/rcsfreeze.1.gz
monster-masher: /usr/share/monster-masher/pixmaps/freeze-box-24.png
monster-masher: /usr/share/monster-masher/pixmaps/freeze-box-32.png
monster-masher: /usr/share/monster-masher/pixmaps/power-up-freeze-24.png
monster-masher: /usr/share/monster-masher/pixmaps/power-up-freeze-32.png
njam: /usr/share/njam/data/freeze.wav
njam: /usr/share/njam/html/freezer.gif
parrot-doc: /usr/share/doc/parrot-doc/examples/benchmarks/freeze.pasm
parrot-doc: /usr/share/doc/parrot-doc/examples/benchmarks/freeze.pl
parrot-doc: /usr/share/doc/parrot-doc/pmc_freeze.pod
perl: /usr/lib/perl/5.8.8/auto/Storable/_freeze.al
perl: /usr/lib/perl/5.8.8/auto/Storable/freeze.al
perl: /usr/lib/perl/5.8.8/auto/Storable/nfreeze.al
perl-tk: /usr/lib/perl5/auto/Tk/Frame/freeze_on_map.al
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/GTK/Calendar/freeze.html
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/GTK/Clist/freeze.html
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/GTK/Layout/freeze.html
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/GTK/Text/freeze.html
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/Gnome/IconList/freeze.html
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0000.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0001.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0002.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0003.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0004.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0005.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0006.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0007.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0008.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0009.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0010.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0011.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0012.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0013.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0014.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0015.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0016.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0017.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0018.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0019.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0020.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0021.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0022.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0023.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0024.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0025.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0026.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0027.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0028.png
pipenightdreams-data: /usr/share/games/pipenightdreams/images/default/freeze_bonus0029.png
pvm-dev: /usr/share/man/man3/pvm_freezegroup.3PVM.gz
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/README.gz
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/bkfile.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/checkextensions.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/checkextensions_win32.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/extensions_win32.ini
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/freeze.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/hello.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/makeconfig.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/makefreeze.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/makemakefile.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/parsesetup.py
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/win32.html
python2.4-examples: /usr/share/doc/python2.4/examples/Tools/freeze/winmakemakefile.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/README.gz
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/bkfile.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/checkextensions.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/checkextensions_win32.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/extensions_win32.ini
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/freeze.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/hello.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/makeconfig.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/makefreeze.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/makemakefile.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/parsesetup.py
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/win32.html
python2.5-examples: /usr/share/doc/python2.5/examples/Tools/freeze/winmakemakefile.py
rcs: /usr/bin/rcsfreeze
rcs: /usr/share/man/man1/rcsfreeze.1.gz
ri1.8: /usr/share/ri/1.8/system/Module/freeze-i.yaml
ri1.8: /usr/share/ri/1.8/system/Object/freeze-i.yaml
ri1.8: /usr/share/ri/1.8/system/Pathname/freeze-i.yaml
ri1.8: /usr/share/ri/1.8/system/XSD/NamedElements/freeze-i.yaml
ri1.9: /usr/share/ri/1.9.0/system/Module/freeze-i.yaml
ri1.9: /usr/share/ri/1.9.0/system/Object/freeze-i.yaml
ri1.9: /usr/share/ri/1.9.0/system/Pathname/freeze-i.yaml
slice2freeze: /usr/bin/slice2freeze
slice2freeze: /usr/share/doc/slice2freeze/README
slice2freeze: /usr/share/doc/slice2freeze/changelog.Debian.gz
slice2freeze: /usr/share/doc/slice2freeze/copyright
slice2freeze: /usr/share/man/man1/slice2freeze.1.gz
slice2freezej: /usr/bin/slice2freezej
slice2freezej: /usr/share/doc/slice2freezej/README
slice2freezej: /usr/share/doc/slice2freezej/changelog.Debian.gz
slice2freezej: /usr/share/doc/slice2freezej/copyright
slice2freezej: /usr/share/man/man1/slice2freezej.1.gz
smail: /usr/lib/smail/unfreezemail
smail: /usr/lib/smail/unfreezemail.O
smail: /usr/sbin/unfreezemail
smail: /usr/share/man/man8/unfreezemail.8.gz
sun-java6-javadb: /usr/share/doc/sun-java6-javadb/html/ref/rreffreezedbproc.html
sun-java6-javadb: /usr/share/doc/sun-java6-javadb/html/ref/rrefunfreezedbproc.html
sun-javadb-doc: /usr/share/doc/javadb/docs/html/ref/rreffreezedbproc.html
sun-javadb-doc: /usr/share/doc/javadb/docs/html/ref/rrefunfreezedbproc.html
xfsprogs: /usr/sbin/xfs_freeze
xfsprogs: /usr/share/man/man8/xfs_freeze.8.gz
root@all:~# 


```

-->
 /usr/share/doc/python2.5/examples/Tools/freeze/freeze.py

You need to install python examples:
```

root@all:/usr/share/doc/python2.5# apt-get install python2.5-examples
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  python2.5-examples
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 651kB of archives.
After this operation, 3768kB of additional disk space will be used.
Get:1 http://ch.archive.ubuntu.com hardy/main python2.5-examples 2.5.2-2ubuntu4 [651kB]
Fetched 651kB in 2s (303kB/s)              
Selecting previously deselected package python2.5-examples.
(Reading database ... 193228 files and directories currently installed.)
Unpacking python2.5-examples (from .../python2.5-examples_2.5.2-2ubuntu4_all.deb) ...
Setting up python2.5-examples (2.5.2-2ubuntu4) ...
root@all:/usr/share/doc/python2.5# cd examples
root@all:/usr/share/doc/python2.5/examples# cd Tools
root@all:/usr/share/doc/python2.5/examples/Tools# cd freeze
root@all:/usr/share/doc/python2.5/examples/Tools/freeze# dir
bkfile.py		  [COLOR="Red"][SIZE="5"]freeze.py[/SIZE][/COLOR]	 makemakefile.py  winmakemakefile.py
checkextensions.py	  hello.py	 parsesetup.py
checkextensions_win32.py  makeconfig.py  README.gz
extensions_win32.ini	  makefreeze.py  win32.html
root@all:/usr/share/doc/python2.5/examples/Tools/freeze# ls
bkfile.py                 [COLOR="Red"][SIZE="6"]freeze.py[/SIZE][/COLOR]      makemakefile.py  winmakemakefile.py
checkextensions.py        hello.py       parsesetup.py
checkextensions_win32.py  makeconfig.py  README.gz
extensions_win32.ini      makefreeze.py  win32.html
root@all:/usr/share/doc/python2.5/examples/Tools/freeze# 

```

---

### Post by johnconnor on 2008-04-27
> **pmasiar said:**
> and you will have to compile py2exe on windows, not on Linux
So if I understand right, the answer to my question is: no, it's impossible. ?

---

### Post by WitchCraft on 2008-04-27
> **johnconnor said:**
> So if I understand right, the answer to my question is: no, it's impossible. ?

No it's very possible. But you didn't yet read the last post.

Copy freeze.py & co to your directory

Execute freeze, --> pass your python script name as command line arguments
--> this creates C-Files + a makefile.

Then you type make, and if there are no errors, you will have your executable... But it will be quite big...

---

### Post by johnconnor on 2008-04-27
Thank you very much, this is the kind of anwser I was looking for, I'm sorry I posted before seeing yours.

---

### Post by scourge on 2008-04-27
I strongly agree with the suggestions to just distribute the source or bytecode in deb and rpm packages. After all, modularity and dynamic linking are an essential part of the Linux philosophy.


> **pmasiar said:**
> BTW  you are still required to provide sources according to GPL.

Not trying to derail the thread, but who said anything about the GPL? It's okay to use whatever license you want for the program, and distributing/embedding a binary-only version of Python is allowed even for commercial purposes.

---

### Post by WitchCraft on 2008-04-27
> **johnconnor said:**
> 
Thank you very much, this is the kind of anwser I was looking for, I'm sorry I posted before seeing yours.


No problem ;-)

As others said, it's however nice to provide python sources, too ;-)

And you should, because sometimes there are errors that do occur only on some system, which then means the user needs to fix the sources...

---

### Post by pmasiar on 2008-04-27
Python bytecode is trivial to decompile (only comments are lost), don't hope to hide your sources (or worse, to provide 'security') by providing bytecode only.

---

### Post by johnconnor on 2008-04-28
I don't want to hide my sources, I'm aware opensource is a great thing! It's just a way to distribute my programs easier

---

### Post by CptPicard on 2008-04-28
> **johnconnor said:**
> I don't want to hide my sources, I'm aware opensource is a great thing! It's just a way to distribute my programs easier

It's a misconception from Windows really that mailing exes around is the easy, best way to distribute programs.. :p too bad Windows doesn't have the Linux-style repository system which makes this a moot point.

Anyway, installing Python shouldn't be too hard...

---

### Post by kumoshk on 2008-10-14
Try cx_freeze. It's better than the normal Python freeze.py, I think. It looks like it may also be able to make Windows executables.

I have some answers for those who wonder why you'd want to do this:

Well, Python isn't the only dependency for many Python programs. Sometimes you need something that isn't easy to get on a particular distribution of Linux in the first place (there's not always a download location for what you need, other than the source code). And, expecting the user to compile a bunch of stuff to get it working isn't always ideal (especially if no one is actually known to have done it other than you). Sometimes the file size for the download is enormous compared with what you actually need out of that download. Plus, you may want to go the commercial route, for some odd reason, and hide your code.

---

### Post by dodle on 2008-12-29
I have a question that is relative to this subject.  As mentioned earlier, when creating windows executables the result is quite a large file.  I was trying to find a way for the newly created executable to look in PATH for the python dll (and other dlls), instead of the .exe's directory or within the .exe itself.

Here is what I do:> Copy python25.dll to C:\Windows
Create my executable making sure to exclude python25.dll
But I can't get my executable to point to C:\Windows\python25.dll, so I just end up with an error that says "LoadLibrary(pythondll) failed".  Does anyone know how I can do this?

---

### Post by slickytail on 2011-04-29
wait... do i just copy and paste this all into terminal, or just the first line.

---

