---
title: "Cannot compile Gnofract4d 3.1.3 from source code"
date: 2013-04-08
forum: Packaging and Compiling Programs
---

### Post by MorningLemon on 2013-04-08
Hi, 
I am new to compiling programs from their source code. I am having a lot of trouble installing Gnofract4d v. 3.1.3. I have installed: libjpeg62-dev, python 3.2-dev, transcode, gcc++, gconf2.0, python-dev.

My current system looks like this:

Kernel: 3.5.0-17-generic (i686)
C Library: unknown
Default C compiler: Gnu C compiler v. 4.7.2
Distro: Linux Mint 14 Nadia
DE: MATE
Processor: AMD Athlon II X2 250 x2 (dual core), 3000.00MHz
Memory: 3.9 GB

The error I get is when I try to extract from the tarball. I have tried "tar xzvf gnofract4d-3.1.3.tar.gz cd gnofract4d-3.1.3 ./setup.py build. It complained. It didn't like it. I have tried creating the folder gnofract4d in /usr/share, and extracting as admin. It complained again. This is what I get when I try either of these methods:

jennifer@HAL ~ $ sudo tar xzvf gnofract4d-3.1.3.tar.gz
[sudo] password for jennifer: 
tar (child): gnofract4d-3.1.3.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jennifer@HAL ~ $ cd Downloads
jennifer@HAL ~/Downloads $ tar xzvf gnofract4d-3.1.3.tar.gz
tar (child): gnofract4d-3.1.3.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jennifer@HAL ~/Downloads $ 


If someone what I am doing wrong, I would greatly appreciate your help as this is becoming very frustrating. 

Thanks,
MorningLemon

---

### Post by steeldriver on 2013-04-08
Are you sure the file you downloaded is [COLOR=#000000]gnofract4d-**3.1.3**.tar.gz not [/COLOR]gnofract4d-**3.13**.tar.gz? (the latest version on their sourceforge site is 3.14.1)

You can use tab completion in the shell i.e. type

```
cd ~/Downloads
tar xzvf gnof
```
and then press the TAB key to show you what actual gnof... files are in the directory - much easier than typing the exact version

In any case, any particular reason you are trying to install it from source? there appear to be deb packages on their sourceforge site e.g.

[http://sourceforge.net/projects/gnofract4d/files/gnofract4d/3.13/](http://sourceforge.net/projects/gnofract4d/files/gnofract4d/3.13/)

---

### Post by MorningLemon on 2013-04-08
> **steeldriver said:**
> Are you sure the file you downloaded is [COLOR=#000000]gnofract4d-**3.1.3**.tar.gz not [/COLOR]gnofract4d-**3.13**.tar.gz? (the latest version on their sourceforge site is 3.14.1)

You can use tab completion in the shell i.e. type

```
cd ~/Downloads
tar xzvf gnof
```
and then press the TAB key to show you what actual gnof... files are in the directory - much easier than typing the exact version

In any case, any particular reason you are trying to install it from source? there appear to be deb packages on their sourceforge site e.g.

[http://sourceforge.net/projects/gnofract4d/files/gnofract4d/3.13/](http://sourceforge.net/projects/gnofract4d/files/gnofract4d/3.13/)


I have tried the 3.14.1, but it is a .deb file, and I get the error message that I have the wrong architecture. It says (paraphrasing) Wrong architecture: AMD 64. I've tried all the .deb files. That would be why I am compiling from source. I had a .deb file that looked promising but Gdebi installer would not allow me to install even though I have every dependency I can think of or have come across. I will give your suggestion a try and see what happens. 

Thanks,
MorningLemon

---

### Post by steeldriver on 2013-04-08
since your system is 32 bit (i686) you would need the i386 deb not the AMD 64 deb

---

### Post by MorningLemon on 2013-04-08
It is package 3.13. Good call. I had not noticed that. 

Thanks :)

---

### Post by MorningLemon on 2013-04-08
Good point. I think I tried the l386 .deb, and that was the one that didn't have dependencies or architectural issues, but Gdebi wouldn't allow an install. The Install button stayed gray and flat (if that makes sense.) I clicked, and no click. So, that's when I decided to try compiling. I will get it especially with help :)

Thank you, 
MorningLemon

---

### Post by schragge on 2013-04-09
Instead of gdebi, try to installl the i386.deb in terminal with
```
sudo dpkg -i gnofract*i386.deb
``` Even if this doesn't work, it will give you a comprehensible error message, so that you will get a clue *why* it cannot be installed, and what else must be installed in order to satisfy dependencies. E.g. on my system it gives:
```

gnofract4d depends on python (<< 2.7); however:
  Version of python on system is 2.7.3-4.

``` This means it needs an older python version than I have installed. Actually, after looking at the source, I can say that it will work with python 2.7 just fine, all you need is to rebuild the package. The source already contains  *debian* directory, so building a new deb package from it shouldn't be a problem.

[highlight]Update[/highlight]
Well, the debian packaging of gnofract4d is an awful hack. I've fixed it and uploaded the deb source [here]("https://www.box.com/s/ioh9l0n4ocd7ja831cbk"). You can try to download .dsc and .debian.tar.xz files from there, put them into a folder, then in the same folder
```

pkg=gnofract4d ver=3.14.1
wget -O ${pkg}_$ver.orig.tar.bz2 http://sourceforge.net/projects/$pkg/files/$pkg/$ver/$pkg-$ver.tar.bz2/download
dpkg-source -x ${pkg}_$ver-1.dsc
cd $pkg-$ver
sudo apt-get install build-essential debhelper devscripts python-all-dev lib{png12,gconf2,jpeg8}-dev
dpkg-buildpackage -us -uc -b
sudo debi

```

---

### Post by MorningLemon on 2013-04-09
This is the error message I get when I run sudo dpkg......

galaxybounce@HAL ~ $ sudo dpkg -i gnofract*i386.deb
dpkg: error processing gnofract*i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gnofract*i386.deb

---

### Post by schragge on 2013-04-09
This means the .deb file is not in your home directory. If you downloaded it with web browser, it's probably in *~/Downloads*:
```
sudo dpkg -i ~/Downloads/gnofract*i386.deb
```

---

### Post by MorningLemon on 2013-04-09
Yep, figured that one out on my own  :) I thin your script is going to work. Thank you for your time.

---

### Post by MorningLemon on 2013-04-09
It worked!!!!!! You are a genius!   :):D:D

---

### Post by Eli_B on 2014-02-03
Hello.

Apologies in advance as I am totally new to Ubuntu.  

In stepping through the Code, I get the error "E: Unable to locate package python-dev-all" on the sudo apt-get statement.  

Would you please describe how to satisfy this dependency?

Thank you very much,
Eli

---

### Post by schragge on 2014-02-04
The package is now called *python-all-dev*.

---

### Post by vasa1 on 2014-02-04
@schragge, nice to see you back :)

---

### Post by co6aka2 on 2014-03-06
> **schragge said:**
> [highlight]Update[/highlight]Well, the debian packaging of gnofract4d is an awful hack...
:lolflag:   But there's another problem...

```

Gnofract4D/test/gnofract4d-3.14.1$ dpkg-buildpackage -us -uc -b
dpkg-buildpackage: source package gnofract4d
dpkg-buildpackage: source version 3.14.1-1
dpkg-buildpackage: source changed by Rachel Mant <dx-mon@users.sourceforge.net>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build gnofract4d-3.14.1
dpkg-checkbuilddeps: Unmet build dependencies: libjpeg62-dev
dpkg-buildpackage: warning: build dependencies/conflicts unsatisfied; aborting
dpkg-buildpackage: warning: (Use -d flag to override.)

```

Attempting to install libjpeg62 requires uninstalling libjpeg8, so... ](*,) 

Shouldn't this work OK with libjpeg8...???

---

### Post by schragge on 2014-03-07
Yes, sure. I've just rebuilt the package with libjpeg8-dev and it seems to work. I'm uploading a new version to box.com. Instead of downloading it once again, you can just edit *debian/control*:
```

[COLOR=green]gnofract4d-3.14.1$[/COLOR] sed -i s/jpeg62/jpeg8/ debian/control

```

@vasa1
Nice to see you, too. Unfortunately, I'm mostly away from the forums these days.

---

