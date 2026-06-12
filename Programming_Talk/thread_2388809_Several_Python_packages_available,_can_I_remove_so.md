---
title: "Several Python packages available, can I remove some of them?"
date: 2018-04-07
forum: Programming Talk
---

### Post by &amp;wP*!) on 2018-04-07
I have found that I have many different Python versions installed on my computer.
```
$ ls -ld /usr/lib/python*
drwxr-xr-x 1 root root 9522 Mär 14 01:30 /usr/lib/python2.7
drwxr-xr-x 1 root root   26 Jul 12  2017 /usr/lib/python3
drwxr-xr-x 1 root root 4036 Jan  6 01:03 /usr/lib/python3.6
drwxr-xr-x 1 root root   22 Jan  6 01:03 /usr/lib/python3.7
```

Questions:
[LIST=1]
[*]Can we say that I actually have only 2 Python versions (2.7 and 3.6)? 3.7 seems to have been installed but its dependency not (because python3.7-minimal was not installed)/
[*]Is there a way to find which other packages use these? I could not manage by the apt-get options.
[*]I think usage of virtual environments is a safe way to handle two different Python versions?
[*]Each Python version has its own virtualenv package. Shall I use **python3-venv** for Python3/3.6 and **python3.7-venv** for Python3.7? That's what I see in the info below.
[*]Some Python3 packages might be dependent on Python2.* packages, right? That's what I have understood from several web sites. If this logic is correct than shall I keep all of them?
[/LIST]

Now if I look at each package:
```
$ sudo apt show python
Package: python
Version: 2.7.14-2ubuntu1
Priority: optional
Section: python
Source: python-defaults
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 641 kB
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Pre-Depends: python-minimal (= 2.7.14-2ubuntu1)
**Depends: python2.7 (>= 2.7.14-1~), libpython-stdlib (= 2.7.14-2ubuntu1)**
Suggests: python-doc (= 2.7.14-2ubuntu1), python-tk (>= 2.7.14-1~)
Conflicts: python-central (<< 0.5.5)
Breaks: update-manager-core (<< 0.200.5-2)
Replaces: python-dev (<< 2.6.5-2)
Homepage: http://www.python.org/
Task: ubuntu-live, ubuntu-usb, samba-server, kubuntu-desktop, kubuntu-full, edubuntu-desktop-gnome, edubuntu-usb, xubuntu-desktop, lubuntu-qt-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntustudio-fonts, ubuntu-gnome-live, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 9m
Download-Size: 140 kB
APT-Manual-Installed: no
APT-Sources: http://de.archive.ubuntu.com/ubuntu artful/main amd64 Packages
Description: interactive high-level object-oriented language (default version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v2.7).
```

Python2.7. Running **python** or **python2.7** show the same version 2.7.14.
```
$ sudo apt show python2.7
Package: python2.7
Version: 2.7.14-2ubuntu2
Priority: optional
Section: python
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 375 kB
**Depends: python2.7-minimal (= 2.7.14-2ubuntu2), libpython2.7-stdlib (= 2.7.14-2ubuntu2), mime-support**
Suggests: python2.7-doc, binutils
Conflicts: python-profiler (<= 2.7.1-2)
Breaks: python-virtualenv (<< 1.7.1.2-2~), vim-athena (<< 2:7.3.547-4), vim-gnome (<< 2:7.3.547-4), vim-gtk (<< 2:7.3.547-4), vim-nox (<< 2:7.3.547-4)
Replaces: python-profiler (<= 2.7.1-2), python2.7-minimal (<< 2.7.3-7~)
Task: ubuntu-live, ubuntu-usb, samba-server, kubuntu-desktop, kubuntu-full, edubuntu-desktop-gnome, edubuntu-usb, xubuntu-desktop, lubuntu-qt-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntustudio-fonts, ubuntu-gnome-live, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 9m
Download-Size: 233 kB
APT-Manual-Installed: no
APT-Sources: http://de.archive.ubuntu.com/ubuntu artful/main amd64 Packages
Description: Interactive high-level object-oriented language (version 2.7)
 Python is a high-level, interactive, object-oriented language. Its 2.7 version
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
```

Python3:
```
$ sudo apt show python3
Package: python3
Version: 3.6.3-0ubuntu2
Priority: important
Section: python
Source: python3-defaults
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 68,6 kB
Provides: python3-profiler
Pre-Depends: python3-minimal (= 3.6.3-0ubuntu2)
**Depends: python3.6 (>= 3.6.3-1~), libpython3-stdlib (= 3.6.3-0ubuntu2), dh-python**
Suggests: python3-doc (>= 3.6.3-0ubuntu2), python3-tk (>= 3.6.3-1~), python3-venv (>= 3.6.3-0ubuntu2)
Replaces: python3-minimal (<< 3.1.2-2)
Homepage: http://www.python.org/
Task: minimal, ubuntu-core, ubuntu-core
Supported: 9m
Download-Size: 8.712 B
APT-Manual-Installed: yes
APT-Sources: http://de.archive.ubuntu.com/ubuntu artful/main amd64 Packages
Description: interactive high-level object-oriented language (default python3 version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python 3 version (currently v3.6).
```

Python3.6. Running **python3** or **python3.6** show the same Python version 3.6.3:
```
$ sudo apt show python3.6
Package: python3.6
Version: 3.6.3-1ubuntu1
Priority: important
Section: python
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 307 kB
**Depends: python3.6-minimal (= 3.6.3-1ubuntu1), libpython3.6-stdlib (= 3.6.3-1ubuntu1), mime-support**
Suggests: python3.6-venv, python3.6-doc, binutils
Task: minimal, ubuntu-core, ubuntu-core
Supported: 9m
Download-Size: 175 kB
APT-Manual-Installed: yes
APT-Sources: http://de.archive.ubuntu.com/ubuntu artful/main amd64 Packages
Description: Interactive high-level object-oriented language (version 3.6)
 Python is a high-level, interactive, object-oriented language. Its 3.6 version
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
```

Python3.7 package is below.
```
$ sudo apt show python3.7
Package: python3.7
Version: 3.7.0~a2-1
Priority: optional
Section: universe/python
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 326 kB
**Depends: python3.7-minimal (= 3.7.0~a2-1), libpython3.7-stdlib (= 3.7.0~a2-1), mime-support**
Suggests: python3.7-venv, python3.7-doc, binutils
Download-Size: 195 kB
APT-Sources: http://de.archive.ubuntu.com/ubuntu artful/universe amd64 Packages
Description: Interactive high-level object-oriented language (version 3.7)
 Python is a high-level, interactive, object-oriented language. Its 3.7 version
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
```

When I type python3.7, I get following:
```
$ python3.7
The program 'python3.7' is currently not installed. You can install it by typing:
sudo apt install python3.7-minimal
```

Any confirmation is appreciated.

---

### Post by monkeybrain20122 on 2018-04-07
First of all, which Ubuntu is this? Are you running 18.04 beta? Secondly how did you install python3.7, since I don't think any Ubuntu comes with 3.7 as its python3 version. If you want two different versions of python3 you'd better use anaconda.

---

### Post by &amp;wP*!) on 2018-04-07
> **monkeybrain20122 said:**
> First of all, which Ubuntu is this? Are you running 18.04 beta? Secondly how did you install python3.7, since I don't think any Ubuntu comes with 3.7 as its python3 version. If you want two different versions of python3 you'd better use anaconda.

I have Lubuntu 17.10 Artful Aardvark (latest), not beta (see my avatar info).
I have not installed 3.7 explicitly. Probably another package which I have installed installed this. That's why I have asked 2nd question, i.e. which other package requires this?
3.7 is broken anyway (see my log above, its minimal package was not installed).

I don't intend to use different Python3.x packages. 

I can use anaconda instead of all Python3.x but as I said above, I want to be sure whether any other package is depedent on Python3.x.

Can you answer my other questions? I would appreciate.

---

### Post by monkeybrain20122 on 2018-04-07
> **pencuse said:**
> I have Lubuntu 17.10 Artful Aardvark (latest), not beta (see my avatar info).
I have not installed 3.7 explicitly. Probably another package which I have installed installed this. That's why I have asked 2nd question, i.e. which other package requires this?



check the outputs for 

```
dpkg -S /usr/lib/python3.7
```

---

### Post by &amp;wP*!) on 2018-04-07
```
$ sudo dpkg -S /usr/lib/python3.7
python3-gdbm:amd64: /usr/lib/python3.7
```

It seems it does not belong to any package.

For 3.6 I get:
```
$ sudo dpkg -S /usr/lib/python3.6
libpython3.6-stdlib:amd64, libpython3.6-minimal:amd64, libpython3.6:amd64, python3-gdbm:amd64, python3.6: /usr/lib/python3.6
```

---

### Post by monkeybrain20122 on 2018-04-07
> **pencuse said:**
> ```
$ sudo dpkg -S /usr/lib/python3.7
python3-gdbm:amd64: /usr/lib/python3.7
```

It seems it does not belong to any package.

For 3.6 I get:
```
$ sudo dpkg -S /usr/lib/python3.6
libpython3.6-stdlib:amd64, libpython3.6-minimal:amd64, libpython3.6:amd64, python3-gdbm:amd64, python3.6: /usr/lib/python3.6
```

It says /usr/lib/python3.7 comes from python3-gdbm and /usr/lib/python3.6 could come from same package, or others, the list just tells you which package may require the file in question,  not which packages actually use it if I understand correctly. So both python3 could belong to python3-gdbm, I don't use 17.10 so I don't know, here in  16.04 only py3.5 is installed and used by python3-gdbm.

You can try to remove and then reinstall python3-gdbm and see whether it reinstalls python3.7

To check if the file is present after reinstalling with ls you need to first run
```
sudo updatedb
```

otherwise ls would give you old info from the last time it updated (maybe yesterday)

**Edited:** you don't need sudo for dpkg -S

---

### Post by &amp;wP*!) on 2018-04-07
Uninstall:
```
$ sudo apt-get remove python3-gdbm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  command-not-found python3-commandnotfound python3-gdbm
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 132 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 185007 files and directories currently installed.)
Removing command-not-found (0.3ubuntu17.10.2) ...
Removing python3-commandnotfound (0.3ubuntu17.10.2) ...
Removing python3-gdbm:amd64 (3.6.3-0ubuntu1) ...
```

Check dir:
```
$ ls -ld /usr/lib/python*
drwxr-xr-x 1 root root 9522 Mär 14 01:30 /usr/lib/python2.7
drwxr-xr-x 1 root root   26 Jul 12  2017 /usr/lib/python3
drwxr-xr-x 1 root root 4036 Jan  6 01:03 /usr/lib/python3.6

```

Reinstall:
```
$ sudo apt-get install python3-gdbm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python3-gdbm-dbg
The following NEW packages will be installed:
  python3-gdbm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13,0 kB of archives.
After this operation, 68,6 kB of additional disk space will be used.
Get:1 http://de.archive.ubuntu.com/ubuntu artful/main amd64 python3-gdbm amd64 3.6.3-0ubuntu1 [13,0 kB]
Fetched 13,0 kB in 0s (47,4 kB/s)     
Selecting previously unselected package python3-gdbm:amd64.
(Reading database ... 184988 files and directories currently installed.)
Preparing to unpack .../python3-gdbm_3.6.3-0ubuntu1_amd64.deb ...
Unpacking python3-gdbm:amd64 (3.6.3-0ubuntu1) ...
Setting up python3-gdbm:amd64 (3.6.3-0ubuntu1) ...
```

Check:
```
$ ls -ld /usr/lib/python*
drwxr-xr-x 1 root root 9522 Mär 14 01:30 /usr/lib/python2.7
drwxr-xr-x 1 root root   26 Jul 12  2017 /usr/lib/python3
drwxr-xr-x 1 root root 4036 Jan  6 01:03 /usr/lib/python3.6
drwxr-xr-x 1 root root   22 Apr  7 20:18 /usr/lib/python3.7
```

Check package:
```
$ sudo dpkg -S /usr/lib/python3.7
python3-gdbm:amd64: /usr/lib/python3.7
**$ sudo updatedb**
$ sudo dpkg -S /usr/lib/python3.7
python3-gdbm:amd64: /usr/lib/python3.7
```

Nothing changed.
I think this is a preliminary library (devel or similar), so I need to focus on 3.6, right?

---

### Post by monkeybrain20122 on 2018-04-07
so after first removing and check python3.7 was not there and it reappeared after reinstalling. So pyhton3-gdbm is using the python3.7 lib in 17.10. I don't see any problem as long as you know where it is from.

---

### Post by &amp;wP*!) on 2018-04-07
> **monkeybrain20122 said:**
> so after first removing and check python3.7 was not there and it reappeared after reinstalling. **So pyhton3-gdbm is using the python3.7 lib in 17.10**. I don't see any problem as long as you know where it is from.

Summary:
On the computer for the 17.10 version of Lubuntu, Python3 has both 3.6 and 3.7. python3-gdbm is used from Python3.7 for 3.6, that's why 3.7 exists. 

Thank you for your help!

---

