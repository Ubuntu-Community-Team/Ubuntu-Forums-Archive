---
title: "Build libinput No compiler. no libraries"
date: 2019-04-29
forum: New to Ubuntu
---

### Post by yoshiki2 on 2019-04-29
Hello. I am trying to build libinput to fix my hardware(touchpad) problems. I follow this code..
```
$ git clone https://gitlab.freedesktop.org/libinput/libinput
$ cd libinput
$ meson --prefix=/usr builddir/
$ ninja -C builddir/
$ sudo ninja -C builddir/ install
sudo systemd-hwdb update
$ ls -l /usr/lib64/libinput.*

```
and I get this errors.. Someone said I have no compiler and libraries were not available.. Any idea how to fix this?
Thanks
```
fredo@fredo-Dell-System-XPS-L321X:~$ git clone https://gitlab.freedesktop.org/libinput/libinput

Command 'git' not found, but can be installed with:

sudo apt install git

fredo@fredo-Dell-System-XPS-L321X:~$ sudo apt install git
[sudo] password for fredo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
Need to get 4,733 kB of archives.
After this operation, 33.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 liberror-perl all 0.17025-1 [22.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.4 [803 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 git amd64 1:2.17.1-1ubuntu0.4 [3,907 kB]
Fetched 4,733 kB in 4s (1,236 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 160747 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17025-1_all.deb ...
Unpacking liberror-perl (0.17025-1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.17.1-1ubuntu0.4_all.deb ...
Unpacking git-man (1:2.17.1-1ubuntu0.4) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.17.1-1ubuntu0.4_amd64.deb ...
Unpacking git (1:2.17.1-1ubuntu0.4) ...
Setting up git-man (1:2.17.1-1ubuntu0.4) ...
Setting up liberror-perl (0.17025-1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up git (1:2.17.1-1ubuntu0.4) ...
fredo@fredo-Dell-System-XPS-L321X:~$ git clone https://gitlab.freedesktop.org/libinput/libinput
Cloning into 'libinput'...
warning: redirecting to https://gitlab.freedesktop.org/libinput/libinput.git/
remote: Enumerating objects: 21631, done.
remote: Counting objects: 100% (21631/21631), done.
remote: Compressing objects: 100% (5392/5392), done.
remote: Total 21631 (delta 16688), reused 20900 (delta 16003)
Receiving objects: 100% (21631/21631), 5.02 MiB | 765.00 KiB/s, done.
Resolving deltas: 100% (16688/16688), done.
fredo@fredo-Dell-System-XPS-L321X:~$ cd libinput
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ meson --prefix=/usr builddir/

Command 'meson' not found, but can be installed with:

sudo apt install meson

fredo@fredo-Dell-System-XPS-L321X:~/libinput$ sudo apt install meson
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ninja-build
The following NEW packages will be installed:
  meson ninja-build
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 309 kB of archives.
After this operation, 1,650 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 ninja-build amd64 1.8.2-1 [93.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 meson all 0.45.1-2 [216 kB]
Fetched 309 kB in 0s (715 kB/s)
Selecting previously unselected package ninja-build.
(Reading database ... 161654 files and directories currently installed.)
Preparing to unpack .../ninja-build_1.8.2-1_amd64.deb ...
Unpacking ninja-build (1.8.2-1) ...
Selecting previously unselected package meson.
Preparing to unpack .../meson_0.45.1-2_all.deb ...
Unpacking meson (0.45.1-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up ninja-build (1.8.2-1) ...
Setting up meson (0.45.1-2) ...
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ meson --prefix=/usr builddir/
The Meson build system
Version: 0.45.1
Source dir: /home/fredo/libinput
Build dir: /home/fredo/libinput/builddir
Build type: native build
Project name: libinput

meson.build:1:0: ERROR: Unknown compiler(s): ['cc', 'gcc', 'clang']
The follow exceptions were encountered:
Running "cc --version" gave "[Errno 2] No such file or directory: 'cc': 'cc'"
Running "gcc --version" gave "[Errno 2] No such file or directory: 'gcc': 'gcc'"
Running "clang --version" gave "[Errno 2] No such file or directory: 'clang': 'clang'"

A full log can be found at /home/fredo/libinput/builddir/meson-logs/meson-log.txt
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ ninja -C builddir/
ninja: Entering directory `builddir/'
ninja: error: loading 'build.ninja': No such file or directory
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ sudo ninja -C builddir/ install
ninja: Entering directory `builddir/'
ninja: error: loading 'build.ninja': No such file or directory
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ sudo systemd-hwdb update
fredo@fredo-Dell-System-XPS-L321X:~/libinput$ ls -l /usr/lib64/libinput.*
ls: cannot access '/usr/lib64/libinput.*': No such file or directory

```

---

### Post by dino99 on 2019-04-30
An old howto, but still can bring you up with the way to follow:
[https://www.reddit.com/r/LinuxOnThinkpad/comments/7bfa8k/tutorial_libinput_thinkpad_improvement_ubuntu_1710/](https://www.reddit.com/r/LinuxOnThinkpad/comments/7bfa8k/tutorial_libinput_thinkpad_improvement_ubuntu_1710/)

indeed, adapt with the actual pathes and used tools.

---

### Post by yoshiki2 on 2019-05-02
Hello, I tried to install libinput to fix my touchpad.. but i get some errors..
I am following the instructions on this page  
[https://www.reddit.com/r/LinuxOnThinkpad/comments/7bfa8k/tutorial_libinput_thinkpad_improvement_ubuntu_1710/](https://www.reddit.com/r/LinuxOnThinkpad/comments/7bfa8k/tutorial_libinput_thinkpad_improvement_ubuntu_1710/)
I am running ubuntu 18.04.2
How could I fix those errors?

```
fredo@fredo-Dell-System-XPS-L321X:~$ sudo apt-get install git meson xserver-xorg-dev doxygen-dev doxygen graphviz libgtk-3-dev check valgrind libunwind-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package doxygen-dev

```

Also.. If i try to continue I get some other errors..
```

fredo@fredo-Dell-System-XPS-L321X:~/compile/libinput$ meson . build/ --prefix=/usr
The Meson build system
Version: 0.45.1
Source dir: /home/fredo/compile/libinput
Build dir: /home/fredo/compile/libinput/build
Build type: native build
Project name: libinput
Native C compiler: cc (gcc 7.4.0 "cc (Ubuntu 7.4.0-1ubuntu1~18.04) 7.4.0")
Build machine cpu family: x86_64
Build machine cpu: x86_64
Fetching value of define "static_assert": _Static_assert
Header <dirent.h> has symbol "versionsort": YES
Header <errno.h> has symbol "program_invocation_short_name": YES
Has header "xlocale.h": NO
Checking if "locale.h" links: YES
Header <sys/ptrace.h> has symbol "PTRACE_ATTACH": YES
Found pkg-config: /usr/bin/pkg-config (0.29.1)
Native dependency libudev found: YES 237
Native dependency mtdev found: YES 1.1.5
Native dependency libevdev found: YES 1.5.8
Library m found: YES
Library rt found: YES
Native dependency libwacom found: YES 0.29
Checking for function "libwacom_get_paired_device": YES
Checking for function "libwacom_get_button_evdev_code": YES
Configuring 80-libinput-device-groups.rules using configuration
Configuring 90-libinput-model-quirks.rules using configuration
Configuring 80-libinput-device-groups-litest.rules using configuration
Configuring 90-libinput-model-quirks-litest.rules using configuration
Header <sys/epoll.h> has symbol "epoll_create1": YES
Program quirks/test-quirks-in-meson.build.sh found: YES (/home/fredo/compile/libinput/quirks/test-quirks-in-meson.build.sh)
Configuring libinput-version.h using configuration
Program install found: YES (/usr/bin/install)
Program doxygen found: YES (/usr/bin/doxygen)
Program dot found: YES (/usr/bin/dot)
Program grep found: YES (/bin/grep)
Configuring libinput.h using configuration
Configuring header.html using configuration
Configuring footer.html using configuration
Configuring customdoxygen.css using configuration
Configuring bootstrap.css using configuration
Configuring libinputdoxygen.css using configuration
Configuring libinput.doxygen using configuration
Program sphinx-build-3 found: NO
Program sphinx-build found: NO

doc/user/meson.build:4:1: ERROR: Problem encountered: Program "sphinx-build" not found or not executable. Try building with -Ddocumentation=false


```

---

### Post by mc4man on 2019-05-02
Your last error is due to not having python3-sphinx package installed.
Odds are you won't be able to build documentation anyway so configure it out (remove the build folder & try again.. i.e
meson . build/ --prefix=/usr -Ddocumentation=false

---

### Post by yoshiki2 on 2019-05-24
I just did a fresh installation of ubuntu 19.04. I booted a fedora 30 usb and my touchpad is working. Seems like the fix to my touchpad is located on fedora 30.
How can I update to libinput 13?

---

