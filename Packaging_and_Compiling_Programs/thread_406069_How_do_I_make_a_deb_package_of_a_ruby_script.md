---
title: "How do I make a deb package of a ruby script?"
date: 2007-04-10
forum: Packaging and Compiling Programs
---

### Post by ceeg on 2007-04-10
I finished a ruby program recently, and I'd like to make a package out of it so a friend of mine can simply apt-get install myprogram from my repository.

Anyone know how I can do this?

---

### Post by WW on 2007-04-11
Here is one way to create a .deb file, using the program **epm**.  First, install epm with the command
```

$ sudo apt-get install epm

```
As an example, I will create a package for a very simple python program  called helloworld.py:
```

#!/usr/bin/env python

#
# helloworld.py
#

print 'Hello, World!'

```
In the directory that contains helloworld.py, create a file called **helloworld.list** that looks like this:
```

%product Hello World
%copyright 2007 by Yours Truly
%vendor Yours Truly
%description This program prints "Hello, World!"
%version 0.1
%readme README
%license LICENSE
%requires python

f 755 root sys /usr/bin/helloworld.py helloworld.py

```
Then, in the same directory, create the files **README** and **LICENSE**. At a minimum, do this:
```

$ touch README
$ touch LICENSE

```
(Of course, you should really put useful information in those files.)

Finally, we use epm to create the package:
```

$ epm -f deb helloworld

```
You might see this warning:
```

epm: Warning - file permissions and ownership may not be correct
     in Debian packages unless you run EPM as root!

```
but the package will work fine (well, it has for me so far).

The package will be created in a subdirectoy; the name of the subdirectory and the package depend on the architecture of your computer. On an Intel computer (running the 2.6 kernel), the directory is **linux-2.6-intel**, and the package is **helloworld-0.1-linux-2.6-intel.deb**.

If you don't want to include "linux-2.6-intel" in the filename of the package, you can use the -n option:
```

epm -n -f deb helloworld

```
This will create a package called **helloworld-0.1.deb**.  (It will still be in the directory linux-2.6-intel.)

You can find out more about epm here: [http://www.easysw.com/epm/](http://www.easysw.com/epm/)

I don't know anything about setting up a repository, so I can't help you with that.

---

### Post by ceeg on 2007-04-11
Well that's certainly a lot easier than the way I ended figuring it out ;)
Thanks a bunch.

---

### Post by scicode on 2007-07-24
hi, thanks for the tutoria WW

after watching [this]("http://showmedo.com/videos/video?name=linyxJensMakingDeb&fromSeriesID=37") wonderful tutorial on how to make deb packages for ubuntu I decided to try epm first.

---

### Post by scicode on 2007-08-06
ok i was very sucessfull in making a nice .deb package of my program ... however epm is missing sections for ubuntu (science, games ...) which is not that bad, but I also discovered on more thing:

if I install python files and execute them **.pyc files** will be created, these are **not removed** when I **remove the package with synaptic** (a warning is issued while removing that some files are left behing). My solution for now is to also include the .pyc files in the installation. Is that correct? I also wonder what happens when I install my main program files into /usr/bin and they do not have an .py extension, will the pyc files still be created and how do I treat these files?

---

### Post by Frak on 2007-08-07
Thanks for the tutorial WW.

---

### Post by charlie763 on 2007-08-28
> **WW said:**
> I don't know anything about setting up a repository, so I can't help you with that.

[Here is an article]("http://www.desktoplinux.com/news/NS5056230026.html") about a service on [Launchpad]("https://launchpad.net/"). From the article:

[INDENT]*Developers upload packages to a PPA and have it built for multiple architectures against the current version of Ubuntu. Each user gets up to 1GB of Personal Package Archive space, which works as a standard Ubuntu software package repository. Free PPAs are available only for free ("libre") software packages.*[/INDENT]

So you don't need to set up your own repository, Launchpad will take care of that for you. This feature is currently available.

---

### Post by charlie763 on 2007-08-29
> **scicode said:**
> ok i was very sucessfull in making a nice .deb package of my program ... however epm is missing sections for ubuntu (science, games ...) which is not that bad, but I also discovered on more thing:

if I install python files and execute them **.pyc files** will be created, these are **not removed** when I **remove the package with synaptic** (a warning is issued while removing that some files are left behing). My solution for now is to also include the .pyc files in the installation. Is that correct? I also wonder what happens when I install my main program files into /usr/bin and they do not have an .py extension, will the pyc files still be created and how do I treat these files?

I have the same problem with the pyc files. Anyone have a more elegant solution?

---

### Post by code-breaker on 2007-09-05
Maybe you can use a prerm shell script to remove the pyc files:

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-maintscripts]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-maintscripts")

---

### Post by charlie763 on 2007-09-05
I think that's exactly what I'll do when I finally get around to making a nice source package that adheres to .deb standards. For now I have it set up  such that the .py files are compiled into .pyc files. The .pyc files are installed instead of the .py files. This solves the derelict-file problem and has the added benefit of being a bit faster the first time it's run. The only problem is that it needs to be compiled for each architecture. Here is my Makefile.
```
gladex : package

package : gladex-0.3.4.deb

gladex-0.3.4.deb : gladex.list # And a bunch of other stuff.
	python -mcompileall .
	sudo epm -n -f deb gladex

install :
	sudo dpkg --install linux-2.6-*/gladex-0.3.4.deb

clean :
	rm -rfv linux-2.6-* *~ *.pyc \#*\#
```

---

### Post by Cappy on 2007-09-08
Thanks for this information! I used it to make a package for my script getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I'm thinking of doing some others.

epm can also be used to run code post-install like this:

```

%postinstall <<EOF
sudo sh /usr/bin/skype.sh
sudo rm /usr/bin/skype.sh
EOF

```

To get my script to install with user permissions "root root" I DID have to run epm with root or else it would make the script permissions "cappy cappy".

---

