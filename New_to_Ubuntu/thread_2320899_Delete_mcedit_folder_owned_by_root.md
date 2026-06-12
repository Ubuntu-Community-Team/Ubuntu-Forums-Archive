---
title: "Delete mcedit folder owned by root"
date: 2016-04-18
forum: New to Ubuntu
---

### Post by ryan168 on 2016-04-18
So I know next to nothing about ubuntu. I wanted to install mcedit on ubuntu 14.04, using this tutorial: [http://www.minecraftforum.net/forums/show-your-creation/video-series-help/technical-help/1715013-how-to-install-mcedit-in-ubuntu](http://www.minecraftforum.net/forums/show-your-creation/video-series-help/technical-help/1715013-how-to-install-mcedit-in-ubuntu)

When I do sudo python mcedit.py, from the desktop directory (where I saved the mcedit folder), i get this error:
python: can't open file 'mcedit.py': [Errno 2] No such file or directory

Can anyone help me please either get mcedit to work, or help me delete the root-owned folders? Is there a good thread to install mcedit?

FYI: I've looked at all kinds of threads for deleting root-owned files. gksudo nautilus and sudo rm have both failed

---

### Post by QDR06VV9 on 2016-04-18
That is a pretty outdated thread...
See this one: [https://github.com/Khroki/MCEdit-Unified](https://github.com/Khroki/MCEdit-Unified)

---

### Post by yetimon_64 on 2016-04-18
> **ryan168 said:**
> ...help me delete the root-owned folders?...  and sudo rm have both failed
You may need to use the command switches -r and -f to recursively (needed for a folder) and forcibly remove such a folder; if you just tried with "rm" without the switches it likely won't work.

**Always be extremely careful when using the "-rf" switch combination with rm**, you can do serious system damage if you don't specify the correct folder to remove.

An example of the command would look like "sudo rm **-rf** mcedit" if issued from the same location as the mcedit folder.

---

### Post by ryan168 on 2016-04-18
runrickus: I downloaded the .zip file, and did everything the readme file said, but when i did python mcedit.py, i got the same error:
python: can't open file 'mcedit.py': [Errno 2] No such file or directory

yetimon_64: Thanks so much, that worked beautifully!

---

### Post by QDR06VV9 on 2016-04-19
> **ryan168 said:**
> runrickus: I downloaded the .zip file, and did everything the readme file said, but when i did python mcedit.py, i got the same error:
python: can't open file 'mcedit.py': [Errno 2] No such file or directory

yetimon_64: Thanks so much, that worked beautifully!
If you still have interest in installing mcedit you will need some depends
```
sudo apt-get install python-opengl python-pygame python-yaml python-numpy
```
You should now be able to run MCEdit with `python mcedit.py` assuming you've installed all the dependencies correctly.
Kind regards

---

### Post by ryan168 on 2016-04-19
Runrickus,
     I ran the code you said:

```
rjslater@rjslater-Inspiron-3551:~$ sudo apt-get install python-opengl python-pygame python-yaml python-numpy
[sudo] password for rjslater: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-opengl is already the newest version.
python-pygame is already the newest version.
python-numpy is already the newest version.
python-yaml is already the newest version.
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb autogen binutils-mingw-w64-i686
  binutils-mingw-w64-x86-64 dmraid firefox-locale-en g++-mingw-w64
  g++-mingw-w64-i686 g++-mingw-w64-x86-64 gcc-mingw-w64 gcc-mingw-w64-base
  gcc-mingw-w64-i686 gcc-mingw-w64-x86-64 gfortran-mingw-w64
  gfortran-mingw-w64-i686 gfortran-mingw-w64-x86-64 gir1.2-json-1.0
  gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 gnat-mingw-w64 gnat-mingw-w64-base
  gnat-mingw-w64-i686 gnat-mingw-w64-x86-64 javascript-common kde-l10n-engb
  kpartx kpartx-boot libdebian-installer4 libdevmapper-event1.02.1
  libdmraid1.0.0.rc16 libjs-jquery libjs-jquery-ui libopts25 libopts25-dev
  lvm2 mingw-w64 mingw-w64-common mingw-w64-i686-dev mingw-w64-x86-64-dev
  python3-pam quilt rdate watershed
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
rjslater@rjslater-Inspiron-3551:~$ python mcedit.py
python: can't open file 'mcedit.py': [Errno 2] No such file or directory

```
I'm still getting the same error. Any ideas?

---

### Post by Tadaen_Sylvermane on 2016-04-19
You aren't specifying the path to the mcedit.py file. You can't do it from ~ unless the file is there. If it's in a folder then you need to be in that folder or specify the path...

~/mcedit/mcedit.py

---

### Post by QDR06VV9 on 2016-04-20
> **Tadaen_Sylvermane said:**
> You aren't specifying the path to the mcedit.py file. You can't do it from ~ unless the file is there. If it's in a folder then you need to be in that folder or specify the path...

~/mcedit/mcedit.py
+1

> **ryan168 said:**
> Runrickus,
     I ran the code you said:

rjslater@rjslater-Inspiron-3551:~$ sudo apt-get install python-opengl python-pygame python-yaml python-numpy
[sudo] password for rjslater: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-opengl is already the newest version.
python-pygame is already the newest version.
python-numpy is already the newest version.
python-yaml is already the newest version.
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb autogen binutils-mingw-w64-i686
  binutils-mingw-w64-x86-64 dmraid firefox-locale-en g++-mingw-w64
  g++-mingw-w64-i686 g++-mingw-w64-x86-64 gcc-mingw-w64 gcc-mingw-w64-base
  gcc-mingw-w64-i686 gcc-mingw-w64-x86-64 gfortran-mingw-w64
  gfortran-mingw-w64-i686 gfortran-mingw-w64-x86-64 gir1.2-json-1.0
  gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 gnat-mingw-w64 gnat-mingw-w64-base
  gnat-mingw-w64-i686 gnat-mingw-w64-x86-64 javascript-common kde-l10n-engb
  kpartx kpartx-boot libdebian-installer4 libdevmapper-event1.02.1
  libdmraid1.0.0.rc16 libjs-jquery libjs-jquery-ui libopts25 libopts25-dev
  lvm2 mingw-w64 mingw-w64-common mingw-w64-i686-dev mingw-w64-x86-64-dev
  python3-pam quilt rdate watershed
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
rjslater@rjslater-Inspiron-3551:~$ python mcedit.py
python: can't open file 'mcedit.py': [Errno 2] No such file or directory

I'm still getting the same error. Any ideas?
Where is the script you downloaded?
While we are here lets clean up a little bit.
```
sudo apt-get autoremove
```
This is a little house cleaning... keeps the package manager happy and avoids future problems.

---

