---
title: "Debian build system newb needs help: python2.5-2.5.1: build-conflicts, failed tests"
date: 2007-06-16
forum: Packaging and Compiling Programs
---

### Post by eddymul on 2007-06-16
I am learning the Debian build system. 

I am trying to rebuild feisty's python2.5-2.5.1-0ubuntu1. After importing the necessary GPG keys, `apt-get source python2.5`, and `dpkg-buildpackage -rfakeroot -uc -b`, I got warnings about build conflicts.
```

dpkg-buildpackage: source package is python2.5
dpkg-buildpackage: source version is 2.5.1-0ubuntu1
dpkg-buildpackage: source changed by Matthias Klose <doko@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.5.1-0ubuntu1
dpkg-checkbuilddeps: Build conflicts: python2.5-xml python-xml
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```

I followed the advice and added `-d`. I got .debs. But I was worried about possible build conflicts.

I found out that the tests/checks are not being run. I hand-edited debian/rules, changing "WITHOUT_CHECK := no". I `tee`-ed the output, and noticed that a bunch of tests failed and there were segfaults after pyexpat.

```

test_profile skipped -- No module named profile
test_profilehooks
test_pty
test_pwd
test_pyclbr
test_pyexpat
make[1]: *** [test] Segmentation fault (core dumped)

```

I still got .debs, but I am now worried about installing them to my system.

My questions:
[LIST=1]
[*]How do I resolve the build conflicts? Am I supposed to uninstall python-xml?
[*]Can I tell `dpkg-buildpackage` to build only python2.5, and not build -dbg, idle, etc?
[*]How do I enforce the tests/checks without hand-editing debian/rules? Is it through shell variables?
[*]I assume that all test are supposed to pass. Is my assumption correct?
[*]I want to compare my test_results with the Ubuntu packager's test_results. Is there a place where I can see that file/log? (Didn't find it in packages.ubuntu.com, and python.org's buildbot only has ia64 dapper).
[/LIST]

---

### Post by eddymul on 2007-06-17
> **eddymul said:**
> After importing the necessary GPG keys, `apt-get source python2.5`, and `dpkg-buildpackage -rfakeroot -uc -b`, I got warnings about build conflicts.

[LIST=1]
[*]How do I resolve the build conflicts? Am I supposed to uninstall python-xml?
[/LIST]

I RTFM, and found out that I can `sudo apt-get build-dep python2.5` before dpkg-buildpackage. And, yes, it uninstalled python-xml (along with serpentine and revelation)   :(

I'm waiting for the new set of test_results...

---

### Post by eddymul on 2007-06-17
> **eddymul said:**
> I'm waiting for the new set of test_results...

I consistently get these results:
```

2 tests failed:
    test_curses test_linuxaudiodev
22 tests skipped:
    test_aepack test_al test_applesingle test_bsddb185 test_cProfile
    test_cd test_cl test_gl test_imgfile test_macfs test_macostools
    test_nis test_pep277 test_plistlib test_profile
    test_scriptpackages test_startfile test_sunaudiodev
    test_unicode_file test_winreg test_winsound test_zipfile64
2 skips unexpected on linux2:
    test_profile test_cProfile
Re-running failed tests in verbose mode
Re-running test 'test_curses' in verbose mode
[?1049h[1;24r[m(B[4l[?7h[H[2J[24;1H[?1049l
[?1l>test test_curses crashed -- <class '_curses.error'>: endwin() returned ERR
Traceback (most recent call last):
  File "../Lib/test/regrtest.py", line 549, in runtest_inner
    the_package = __import__(abstest, globals(), locals(), [])
  File "/home/eddymul/Desktop/lab/python2.5-2.5.1/Lib/test/test_curses.py", line 273, in <module>
    curses.endwin()
error: endwin() returned ERR
Re-running test 'test_linuxaudiodev' in verbose mode
test test_linuxaudiodev crashed -- <class 'linuxaudiodev.error'>: (0, 'Error')
Traceback (most recent call last):
  File "../Lib/test/regrtest.py", line 549, in runtest_inner
    the_package = __import__(abstest, globals(), locals(), [])
  File "/home/eddymul/Desktop/lab/python2.5-2.5.1/Lib/test/test_linuxaudiodev.py", line 92, in <module>
    test()
  File "/home/eddymul/Desktop/lab/python2.5-2.5.1/Lib/test/test_linuxaudiodev.py", line 89, in test
    play_sound_file(findfile('audiotest.au'))
  File "/home/eddymul/Desktop/lab/python2.5-2.5.1/Lib/test/test_linuxaudiodev.py", line 53, in play_sound_file
    a.write(data)
error: (0, 'Error')
warning: DBTxn aborted in destructor.  No prior commit() or abort().

```

[LIST]
[*]test_curses: No idea why it's failing...
[*]test_profile skipped -- No module named profile
[*]test_cProfile skipped -- No module named pstats
[*]test_linuxaudiodev: Probably needs to be run as real root instead of fakeroot.
[/LIST]

I noticed that the Debian buildd passes these tests (albeit building slightly different version of python). Hm....

I'll try rebuilding it as root using `sudo -s`.

My test environment:
```

========== test environment ============
SSH_AGENT_PID=5360
TERM=xterm
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
MAKEFLAGS=
PRIORITY=250
DEB_BUILD_ARCH_OS=linux
DEB_HOST_GNU_SYSTEM=linux-gnu
GTK_RC_FILES=/etc/gtk/gtkrc:/home/eddymul/.gtkrc-1.2-gnome2
WINDOWID=86001434
GTK_MODULES=gail:atk-bridge
NVER=2.6
USER=eddymul
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-OcuEmv5322/agent.5322
GNOME_KEYRING_SOCKET=/tmp/keyring-lSAuhO/socket
MAKELEVEL=1
DEB_BUILD_ARCH_CPU=i386
SESSION_MANAGER=local/elendil:/tmp/.ICE-unix/5322
USERNAME=eddymul
MFLAGS=
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
DEB_BUILD_ARCH=i386
_=/usr/bin/env
GDM_XSERVER_LOCATION=local
PWD=/home/eddymul/Desktop/lab/python2.5-2.5.1
DEB_HOST_ARCH=i386
DEB_HOST_GNU_TYPE=i486-linux-gnu
PVER=python2.5
GDMSESSION=default
HISTCONTROL=ignoreboth
DEB_HOST_GNU_CPU=i486
SHLVL=2
HOME=/home/eddymul
DEB_HOST_ARCH_OS=linux
GNOME_DESKTOP_SESSION_ID=Default
DEB_BUILD_GNU_CPU=i486
LOGNAME=eddymul
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-zFlvC7n9TQ,guid=2635f2ecf9adbd9ee290de004674bf64
DEB_BUILD_GNU_SYSTEM=linux-gnu
LESSOPEN=| /usr/bin/lesspipe %s
VER=2.5
DISPLAY=:0.0
DEB_BUILD_GNU_TYPE=i486-linux-gnu
LESSCLOSE=/usr/bin/lesspipe %s %s
DEB_HOST_ARCH_CPU=i386
COLORTERM=gnome-terminal
XAUTHORITY=/home/eddymul/.Xauthority
========================================

```

---

