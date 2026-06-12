---
title: "pyinstaller 1.3 compile problem"
date: 2007-11-04
forum: Programming Talk
---

### Post by Siph0n on 2007-11-04
Hi. I am not sure if this should go here, but I will post anyway... Please feel free to move to the correct forum if it's in the wrong place.

I wrote a python script at my work, on a windows computer, but I want to convert it to an exe file so that I can share it with my coworkers, that don't have python installed. I decided to go with pyinstaller for this, but can't seem to get it to compile. I read the readme and it said to go to the source/linux directory and type python ./Make.py . After I type that I get this: WARNING: could not find Python static library at: /usr/lib/python2.5/config/libpython2.5.a

I looked in the /usr/lib/python2.5/config directoy and there is no libpython2.5.a file.... There is only a Makefile file in that directory. Any ideas? Thanks in advance!

---

### Post by evymetal on 2007-11-04
> **Siph0n said:**
> 
I looked in the /usr/lib/python2.5/config directoy and there is no libpython2.5.a file.... There is only a Makefile file in that directory. Any ideas? Thanks in advance!

fairly sure you need to rub pyinstall on a windows box (which won't have a filepath /usr/ . You may be able to get it to compile on linux by installing python for windows and gcc under wine, but I've only compiled exes on a windows XP box.

As a warning, I still get complaints about missing windows system files whenever I compile (once it's up and running), but the apps always run fine.

---

### Post by Siph0n on 2007-11-05
The pyInstallers web page says I can use it on linux or windows.... I am at work now, and sort of figured it out. I don't have access to add the location of the python executable file to my $PATH variable, so I had to copy the python exec to the pyInstaller directory. It made the executable, but I need python25.dll in the same directory to be able to run it. Does this seem correct? I would of thought I would end up with a standalone executable that anyone running windows could run...

---

