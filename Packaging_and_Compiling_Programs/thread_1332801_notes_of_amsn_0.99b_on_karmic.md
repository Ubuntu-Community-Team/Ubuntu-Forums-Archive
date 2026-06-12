---
title: "notes of amsn 0.99b on karmic"
date: 2009-11-20
forum: Packaging and Compiling Programs
---

### Post by Claus7 on 2009-11-20
Hello,

here I'll post some notes on the installation of amsn svn 0.99b package in karmic koala.

In synaptic you can find version 0.98.1, which you can install with one click away. In case you want to experiment with 0.99b then you have to do the following:

i)download the source code from amsn website
ii)untar the file wherever you like (if you want to have both 0.98 and 0.99  versions, then untar the file in a place where it won't hinder other applications)
iii)open a terminal and enter inside the untared directory.
iv) type ./configure

In that step I faced dependency problems even though they were installed. In order to avoid that I had to do the following:
* install libgstfarsight0.10-dev (it wasn't installed)
* configure with the command:
  ```
./configure --with-tk=/usr/lib/tk8.5 --with-tcl=/usr/lib/tcl8.5/
```

Then I typed make.

So if I want to launch 0.99b, I enter in the untared directory and type ./amsn

Regards!

---

### Post by Claus7 on 2010-02-20
Hello,

Facing freezing problems on karmic about audio support, I updated the script I created some years ago, trying to install amsn from source, hoping that audio problem will vanish. Unfortunately I was not able to solve the snack error, as snack stubbornly refuses to be installed properly on karmic using the source code of this library. 

This script is intended to use tk and tck as well as snack from the source code. It does not take into account dependencies that they are supposed to be installed from synaptic in karmic.

Problems encountered and solved:
1)buggy file in generic directory of snack:
[https://bugs.launchpad.net/ubuntu/+source/snack/+bug/437336](https://bugs.launchpad.net/ubuntu/+source/snack/+bug/437336)
[http://bugs.gentoo.org/show_bug.cgi?id=270839](http://bugs.gentoo.org/show_bug.cgi?id=270839)
2)problem in launching amsn due to incompatibility of tk and tcl library versions -> latest versions were used
[https://bugzilla.redhat.com/show_bug.cgi?id=457286](https://bugzilla.redhat.com/show_bug.cgi?id=457286)

After installation another library was needed, yet launching amsn this solves that problem.

Helpful links:
[http://www.opensound.com/forum/viewtopic.php?f=3&t=3371](http://www.opensound.com/forum/viewtopic.php?f=3&t=3371)
[http://www.amsn-project.net/forums/index.php?topic=4539.0](http://www.amsn-project.net/forums/index.php?topic=4539.0)
[http://www.amsn-project.net/forums/index.php?topic=5697.0](http://www.amsn-project.net/forums/index.php?topic=5697.0)
[http://www.amsn-project.net/forums/index.php?topic=4969.0](http://www.amsn-project.net/forums/index.php?topic=4969.0)
[http://www.amsn-project.net/forums/index.php?topic=4958.0](http://www.amsn-project.net/forums/index.php?topic=4958.0)

[http://www.amsn-project.net/forums/index.php?topic=5803.0](http://www.amsn-project.net/forums/index.php?topic=5803.0)
[http://www.amsn-project.net/forums/index.php/topic,3299.45.html](http://www.amsn-project.net/forums/index.php/topic,3299.45.html)

Regards!

---

### Post by Claus7 on 2010-02-24
...some corrections...

helpful thread:
[http://www.amsn-project.net/forums/index.php?topic=3299.30](http://www.amsn-project.net/forums/index.php?topic=3299.30)

---

### Post by megaa on 2010-03-01
It's really useful info 

[http://www.youtubeblasterpro.com/](http://www.youtubeblasterpro.com/)

---

