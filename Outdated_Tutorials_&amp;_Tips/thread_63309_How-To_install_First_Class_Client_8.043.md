---
title: "How-To install First Class Client 8.043"
date: 2005-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by krusbjorn on 2005-09-07
[COLOR="Red"]Edit: Note that this how-to is hopelessly deprecated.[/COLOR]

Needed FirstClass for school, so i fiddeled a little with the dependencies in the deb file.

This should work:

sudo apt-get install libqt3c102-mt
wget [http://johannes.raftegard.se/fcc.deb](http://johannes.raftegard.se/fcc.deb)
sudo dpkg -i fcc.deb
sudo ln -s /opt/firstclass/fcc /usr/bin/fcc

You may need to install more packages than libqt3c102-mt, but that was the only one i needed, and my system is still pretty fresh.

Type fcc to execute.

Good luck!

---

### Post by Nate53085 on 2006-01-07
Note that in breezy, in order to install this package I had to install xlibs by hand first

sudo apt-get install xlibs

Then it worked fine for me.

---

### Post by ecstatic on 2006-02-26
Ok, I did everything that was said above and when I typed in fcc from where I was in the Terminal, this came up:

fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

what exactly did I do wrong and how can this be fixed exactly?  I installed xlibs before I went through everything else.

---

### Post by mistab1034 on 2006-03-10
I'm not sure what repository exactly, but if you uncomment all the repositories of the default 5.10 install there is a Firstclass Client package which installed fine for me.

#sudo apt-get install fcc
#sudo ln -s /opt/firstclass/fcc /usr/bin/fcc

---

### Post by ZiGz on 2006-04-03
These instructions in the First Post worked for me.

Thanks

---

### Post by _linux_ on 2006-04-08
It doesn't work for me! :(  It aborts with error 11 when I run it! Anyone know what's wrong?

---

### Post by aysiu on 2006-04-08
[QUOTE=_linux_]It doesn't work for me! :(  It aborts with error 11 when I run it! Anyone know what's wrong?[/QUOTE] Can you copy and paste everything in your terminal? Exactly what you typed and the exact error you got?

---

### Post by KeplerNiko on 2006-04-08
I am attempting to install the FirstClass Client 7.1 (fcc_7.1-17-i386.deb created from an RPM).  I'm not installing the latest version, 8.043, because it enables system administrators to disable the saving of login usernames/passwords and my university has done that.

I'm running into the same problem with libqt3c102, I think.

I solved it on another system by (sym)linking libqt3c102-mt with libqt3c or whatever version will actually install on an Ubuntu install, but I don't know how to do that myself and I can't find the instructions online that I originally followed.

This problem was also encountered while installing Opera, but the best solution for that now seems to be to add the Opera repository and installing it through apt-get.  However, as far as I can tell there is no equivalent for fcc.

What would be the proper way of "telling" the system (through links) to use libqt3c when it looks for libqt3c102-mt?

(I can install fcc by forcing it to ignore dependencies and use it without any problems whatsoever, but every time I apt-get it forces me to uninstall it.)

Edit:
Here's what my terminal says:

> root@ubuntugw:/usr/local/src # dpkg -i fcc_7.1-17_i386.deb
Selecting previously deselected package fcc.
(Reading database ... 94284 files and directories currently installed.)
Unpacking fcc (from fcc_7.1-17_i386.deb) ...
dpkg: dependency problems prevent configuration of fcc:
 fcc depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing fcc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fcc


---

### Post by _linux_ on 2006-04-08
[QUOTE=aysiu]Can you copy and paste everything in your terminal? Exactly what you typed and the exact error you got?[/QUOTE]
Here it is:

```
jason@edubuntu:~$ fcc
fcc: Received signal 11 (aborting)...
Aborted
```

Hope it helps.

---

### Post by krusbjorn on 2006-04-08
[QUOTE=_linux_]Here it is:

```
jason@edubuntu:~$ fcc
fcc: Received signal 11 (aborting)...
Aborted
```

Hope it helps.[/QUOTE]

I got that error about half a year ago, and didnt find any solution, so i had to go back to the horrible browser frontend. Anyways, this guide is really old and there are probably better sources to get the client working.

---

### Post by aysiu on 2006-04-08
Maybe you can try downloading [this](http://public.www.planetmirror.com/pub/ubuntu/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.3-7ubuntu3_i386.deb) to your desktop and then doing this: ```
cd ~/Desktop
sudo dpkg -i libqt3c102-mt_3.3.3-7ubuntu3_i386.deb
```

---

### Post by KeplerNiko on 2006-04-09
Nope, libqt3c102-mt won't install:

```
root@ubuntugw:/home/ywesterfield # sudo dpkg -i libqt3c102-mt_3.3.3-7ubuntu3_i386.deb
dpkg: considering removing libqt3-mt in favour of libqt3c102-mt ...
dpkg: no, cannot remove libqt3-mt (--auto-deconfigure will help):
 ksirtet depends on libqt3-mt (>= 3:3.3.4)
  libqt3-mt is to be removed.
dpkg: regarding libqt3c102-mt_3.3.3-7ubuntu3_i386.deb containing libqt3c102-mt:
 libqt3c102-mt conflicts with libqt3-mt
  libqt3-mt (version 3:3.3.4-8ubuntu5) is installed.
dpkg: error processing libqt3c102-mt_3.3.3-7ubuntu3_i386.deb (--install):
 conflicting packages - not installing libqt3c102-mt
Errors were encountered while processing:
 libqt3c102-mt_3.3.3-7ubuntu3_i386.deb
```

I mean, I could probably force it, but that would more than likely result in another situation where FCC gets removed every time I run apt-get.

I think the symlinking will fix it, I just don't know what/where I need to symlink.

---

### Post by _linux_ on 2006-04-09
[QUOTE=KeplerNiko]Nope, libqt3c102-mt won't install:

```
root@ubuntugw:/home/ywesterfield # sudo dpkg -i libqt3c102-mt_3.3.3-7ubuntu3_i386.deb
dpkg: considering removing libqt3-mt in favour of libqt3c102-mt ...
dpkg: no, cannot remove libqt3-mt (--auto-deconfigure will help):
 ksirtet depends on libqt3-mt (>= 3:3.3.4)
  libqt3-mt is to be removed.
dpkg: regarding libqt3c102-mt_3.3.3-7ubuntu3_i386.deb containing libqt3c102-mt:
 libqt3c102-mt conflicts with libqt3-mt
  libqt3-mt (version 3:3.3.4-8ubuntu5) is installed.
dpkg: error processing libqt3c102-mt_3.3.3-7ubuntu3_i386.deb (--install):
 conflicting packages - not installing libqt3c102-mt
Errors were encountered while processing:
 libqt3c102-mt_3.3.3-7ubuntu3_i386.deb
```

I mean, I could probably force it, but that would more than likely result in another situation where FCC gets removed every time I run apt-get.

I think the symlinking will fix it, I just don't know what/where I need to symlink.[/QUOTE]
I found a thread in the Skype forums that said how to symlink liblibqt3-mt. Better go Google it.

---

### Post by _linux_ on 2006-04-10
Okay, I found this:

Change the DEBIAN/control file to check for the libqt3-mt library:
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)

But how do you extract and repackage the .deb file?

---

### Post by whereareyoutakingme on 2006-04-25
[COLOR="Red"][I]Needed FirstClass for school, so i fiddeled a little with the dependencies in the deb file.

This should work:

sudo apt-get install libqt3c102-mt
wget [http://johannes.raftegard.se/fcc.deb](http://johannes.raftegard.se/fcc.deb)
sudo dpkg -i fcc.deb
sudo ln -s /opt/firstclass/fcc /usr/bin/fcc

You may need to install more packages than libqt3c102-mt, but that was the only one i needed, and my system is still pretty fresh.

Type fcc to execute.

Good luck!


Note that in breezy, in order to install this package I had to install xlibs by hand first

sudo apt-get install xlibs

Then it worked fine for me[/I][/COLOR].

**i tried all this and it seemed to work just fine, but whenever i click on the first class menu option...or type fcc in the terminal...it opens a taskbar button at the bottom of my screen, sits there for a moment and then goes away.  any suggestions, i REALLY need first class for school!!!**


[COLOR="Red"][I]Maybe you can try downloading this to your desktop and then doing this: 
Code:
cd ~/Desktop
sudo dpkg -i libqt3c102-mt_3.3.3-7ubuntu3_i386.deb[/I][/COLOR]

**when i went there, it said that the file i want couldn't be found**

---

