---
title: "HOWTO: Install latest aMule"
date: 2005-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ow50 on 2005-03-29
I wrote this before noticing in [another thread](http://www.ubuntuforums.org/showthread.php?t=22571) that the aMule in Hoary repositories is newer than its version number. However, some people might still want the very latest version.

aMule is approaching a stable 2.0 final. The devs are mostly fixing bugs, so cvs is probably more stable than the latest release. With the wx in Hoary, aMule is Gtk2. Unicode works (finally) in aMule. Here's how to get the latest aMule:

1. Install some wx widgets packages, if you don't already have them. Probably the following:
```
sudo apt-get install libwxgtk2.5-dev libwxgtk2.5.3 wx2.5-headers
```

2. Fix your wx installation by adding the missing 'archive.h' file. See [aMule thread](http://forum.amule.org/thread.php?threadid=5139&sid=7540c31dd20e29d6a08410bc555753ce).
```
cd /usr/include/wx-2.5/wx/
sudo wget -O archive.h 'http://cvs.wxwidgets.org/viewcvs.cgi/*checkout*/wxWidgets/include/wx/archive.h?rev=1.1&only_with_tag=DEBIAN_2_5_3_2'
```

3. Get the latest aMule cvs tarball from [http://www.hirnriss.net/?area=cvs](http://www.hirnriss.net/?area=cvs). Install using the traditional
```
./configure
make
sudo make install
```
or check additional options with
```
./configure --help
```

---

### Post by Michael on 2005-03-29
```
michael@ubuntu:~/Downloads/amule-cvs$ make
make: *** No targets specified and no makefile found.  Stop.

```

What do I do?

---

### Post by jeremy on 2005-03-29
You could try downloading the .deb near the bottom of [http://www.amule.org/files/files.php?cat=15](http://www.amule.org/files/files.php?cat=15)
then do;
$sudo dpkg -i [path_to_.deb]

---

### Post by ow50 on 2005-03-29
[QUOTE=Michael]```
michael@ubuntu:~/Downloads/amule-cvs$ make
make: *** No targets specified and no makefile found.  Stop.

```
What do I do?[/QUOTE]

You probably got some error with the './configure'. Post some of the last lines of the output (ones containing the text 'error').

---

### Post by Linux O)o_O7 on 2006-11-05
I just used the add and remove software in Ubuntu to install amule. Worked perfectly and no problems at all. 

Why can't everyone else do the same?

---

### Post by Angafirith on 2006-11-05
It's generally a good idea to look at the date on a post.

While installing amule might be relatively simple now, it may not have been so back in March of 2005.

---

### Post by Linux O)o_O7 on 2006-11-06
lol you can tell I am new here.

Sorry about that.

Yeah I tried to install it myself last year on two Linux distros and I failed. Actually tried on Ubuntu the other day and I wasn't sure how to.

Thanks to this new distro release there is a load of useful basic / essential software.

Ubuntu is the best :mrgreen:

---

### Post by serid on 2007-02-21
Hi,

After ./configure I get an error:

"checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables"

What should I do about it ?

Thanks,

Adrian

---

