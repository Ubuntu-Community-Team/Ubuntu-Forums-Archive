---
title: "Installing dependencies not working"
date: 2013-12-31
forum: Packaging and Compiling Programs
---

### Post by toonamitom on 2013-12-31
I'm trying to compile Pidgin from source. I've tried following a tutorial ([http://www.howtogeek.com/106526/how-to-resolve-dependencies-while-compiling-software-on-ubuntu/](http://www.howtogeek.com/106526/how-to-resolve-dependencies-while-compiling-software-on-ubuntu/)) but it doesn't seem to be working.

I navigate to my Pidgin folder and use auto-apt and configure, which should install the dependencies as needed. The terminal zooms through all the stuff, but eventually it stops and I have to manually install something. Isn't it possible to get this installation to be a fully automatic? I tried using apt-get build-dep, but configure it still halts. 

Right now, it says
```
checking for FARSIGHT... no
Install the necessary gstreamer and farsight packages first.


```
And I can't even install this one (libtelepathy-farstream-dev) manually... perhaps because the name has changed to farstream instead of farsight? I'm stuck and would appreciate any feedback!

---

### Post by damage3025 on 2013-12-31
If you know how to code, you are more or less a software developer/programmer/researcher/system administrator, you should look at configure.ac/configure.in when you get stuck.
That's where you can really see how the tests of generated configure script are performed; not all tests are well-written and not all tests can properly trigger auto-apt.

If you do not have a strong background in computer but still want to compile some software from source, please keep in mind that auto-apt "magic" can definitely fail.
Alternative approaches are:
 * sudo apt-get build-dep package-name
 * tell people your exact Ubuntu version and exact source package (usually a tarball) you want to build; people may give you a walkthrough

---

### Post by toonamitom on 2013-12-31
Thanks for the advice. I've worked with Python before and found it really easy to install dependencies. What I'm finding with Ubuntu is that installing dependencies is a rabbit hole nightmare.

I do sudo apt-get build-dep pidgin. It installs 15 packages. Then I cd to pidgin-2.10.3 and attempt to ./configure, but I get the same error as before:
```

checking for FARSIGHT... no
configure: error: 
Dependencies for voice/video were not met.
Install the necessary gstreamer and farsight packages first.
Or use --disable-vv if you do not need voice/video support.

```

I realize I can disable support, but I don't want to. I want farsight to be installed, automatically if possible. I tried to install it manually and it has its own dependencies that have their own configures which prompt errors.

I'm using Ubuntu 12.04.3 LTS

---

### Post by oldos2er on 2013-12-31
Moved to Packaging & Compiling Programs because compiling is not generally an Absolute Beginner's task.

---

### Post by Yellow Pasque on 2014-01-06
1. Why are you trying to build pidgin 2.10.3 when it's already in Precise repo?
2. The Debian packagers who were building pidgin 2.10.3 for Precise ran into the same issue, so there's a nice patch (attached). (I think they call that 'standing on the shoulders of giants' or something like that).

---

### Post by toonamitom on 2014-01-07
Thanks for your help. I ended up compiling and installing several projects and had to swap versions for some things, but eventually I found a configuration that worked.

---

### Post by toonamitom on 2014-01-12
If anyone else comes across this thread with the same problem, what you should do is simply download the latest version of the Pidgin source code, which can be found here: [http://sourceforge.net/projects/pidgin/files/Pidgin/2.10.7/pidgin-2.10.7.tar.bz2/download](http://sourceforge.net/projects/pidgin/files/Pidgin/2.10.7/pidgin-2.10.7.tar.bz2/download)

Any more help should be found here: [http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)[URL="http://sourceforge.net/projects/pidgin/files/Pidgin/2.10.7/pidgin-2.10.7.tar.bz2/download"]
[/URL]

---

