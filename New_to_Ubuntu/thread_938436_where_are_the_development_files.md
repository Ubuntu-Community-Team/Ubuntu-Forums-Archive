---
title: "where are the development files"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-04
hi,

i download rythmbox dev files from synaptic and it is installed, where can i go and have a look at them in my system. i dont know where those files are stored...

---

### Post by RealPSL on 2008-10-04
If you know the package name. Run this command from the terminal
```
dpkg --listfiles package_name
```

As an example

```
dpkg --listfiles gdm
```

---

### Post by luckydeveloper on 2008-10-05
i am asking the location.. cos i have downloaded several development files for many softwares like rythmbox, vlc, etc. so please help me to find out **_*where*_** those files are installed...

---

### Post by jerome1232 on 2008-10-05
If you trying to get the source code for the program you would do: (not as root)
```
apt-get source rhythmbox
```
That will download the source code to your ~/

If you want to know where a package installs files try the locate and which commands

```
which packagename
locate packagename
```

---

### Post by luckydeveloper on 2008-10-05
thanks... ok. i understood about sources....
then what are development files... supppose in gtkworld...the dev files mean the libraries used to create gtk apps am i right ?....but in application software world...what are dev files (just for example something like vlc-dev) ... how can they be used...why should we have them in the repositories

---

### Post by jerome1232 on 2008-10-05
The -dev packages are used to allow building programs from source.

Say you wanted to build rythmbox from source and it depends on some other packages to be installed. 
In order to compile rhythmbox you will need those packages along with their  development versions installed. I'm guessing they contain functions/headers I have no idea I'm not a programmer (unless you count 'hello world' in python :) )

---

### Post by cariboo on 2008-10-05
Source files that you download using apt, usually end up in /usr/src.

Jim

---

### Post by jerome1232 on 2008-10-05
Oh every time I tried it they ended up in my home directory so I assumed that was where they normally went.


edit: I checked the man page to be sure, when downloaded using apt-get source package name it just downloads the newest source code it can find to the current dirctory

> source
           source causes apt-get to fetch source packages. APT will examine
           the available packages to decide which source package to fetch. It
           will then find and download into the current directory the newest
           available version of that source package. Source packages are
           tracked separately from binary packages via deb-src type lines in
           the sources.list(5) file. This probably will mean that you will not
           get the same source as the package you have installed or as you
           could install. If the --compile options is specified then the
           package will be compiled to a binary .deb using dpkg-buildpackage,
           if --download-only is specified then the source package will not be
           unpacked.

           A specific source version can be retrieved by postfixing the source
           name with an equals and then the version to fetch, similar to the
           mechanism used for the package files. This enables exact matching
           of the source package name and version, implicitly enabling the
           APT::Get::Only-Source option.

           Note that source packages are not tracked like binary packages,
           they exist only in the current directory and are similar to
           downloading source tar balls.

---

