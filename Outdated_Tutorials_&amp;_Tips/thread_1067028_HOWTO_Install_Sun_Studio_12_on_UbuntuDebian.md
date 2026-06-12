---
title: "HOWTO: Install Sun Studio 12 on Ubuntu/Debian"
date: 2009-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Filmorependrgn on 2009-02-11
The latest Sun Studio has two huge advantages:

[LIST=1]
[*]It's [free]("http://developers.sun.com/sunstudio/") (as in beer)
[*]It's Linux x86/x86_64 compatable
[/LIST]

This means some ancient Fortran that was previously trapped on Sparc machines can now be ported to Linux boxes without having to muck through miles of uncommented code! (This guide only covers i386)

Here's the basic procedure:
[LIST=1]
[*]Download dependencies
[*]Download Sun Studio 12
[*]Uncompress the SunStudio install suite
[*]Ignore the builtin install program and use [FONT="Courier New"]alien[/FONT] to install the base programs
[*]Ignore the auto-patcher and use [FONT="Courier New"]alien[/FONT] to install the patches
[/LIST]

[SIZE="6"]Download dependencies[/SIZE]
There's really not a lot of dependencies. Just [FONT="Courier New"]alien[/FONT] I think. The installer, if you want to tinker with it, requires [FONT="Courier New"]gawk[/FONT] and Sun Java 6.

[SIZE="5"]Install [FONT="Courier New"]alien[/FONT][/SIZE]
[FONT="Courier New"]alien[/FONT] is a nice program that will install an RPM package as a Debian package. To install it simply do
```
sudo apt-get install alien
```

[SIZE="5"](Optional?) Download Sun Java 6[/SIZE]
Sun Java 6 is available in the default Ubuntu repositories, or in Unstable for Debian. NOTE: If you want to install Sun Java 6 without going full-unstable, look up info on Apt-pinning.

```
sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-jdk  sun-java6-bin
```
NOTE: If you want to tinker with the installer, you'll probably need to install all the other java6 packages (except the document package)
NOTE: The plugin package is included for good measure.


[SIZE="5"](Optional) Download [FONT="Courier New"]gawk[/FONT][/SIZE]
This one is easy
```
sudo apt-get install gawk
```

[SIZE="6"]Download Sun Studio 12[/SIZE]
On the [Sun Studio website]("http://developers.sun.com/sunstudio/") you can find links to download version 12 for free, provided you sign up as a SDN member, which is also free.

You'll want the package download. As of this writing, the file they give you is `[FONT="Courier New"]SunStudio12ml-linux-x86-200709-pkg.tar.bz2[/FONT]'.


[SIZE="6"]Uncompress the installer files[/SIZE]
These files get extracted into the current directory, so we'll make a directory for us to use. The location of this temporary directory does not matter.
```
$ mkdir tmpss; cd tmpss
```
Now we're ready to extract the installer files
```
tar -xjvf <PATH TO INSTALLER FILE>/SunStudio12ml-linux-x86-200709-pkg.tar.bz2
```

[SIZE="6"]Install the base system using [FONT="Courier New"]alien[/FONT][/SIZE]
There are a bunch of RPMs we need to install. This guide assumes you want to install everything. We simply use [FONT="Courier New"]alien[/FONT] and tell it to install all the Linux packages except the international ones.
```
alien -i `find install-intel-Linux/packages-intel-Linux -name "sun-*[!(zh|ja)]-12.0-1.i386.rpm"`
```

[SIZE="6"]Install the patches using [FONT="Courier New"]alien[/FONT][/SIZE]
Now we'll do the same thing with the patches, but we'll include all i386 and all noarch packages.

```
 alien -i `find  install-intel-Linux/product-patches-intel-Linux -name "*[ (i386|noarch) ].rpm"`
```

Viola!

You now have Sun Studio 12 installed to [FONT="Courier New"]/opt/sun/sunstudio12[/FONT]

You may want to add [FONT="Courier New"]/opt/sun/sunstudio12/bin[/FONT] to your $PATH and [FONT="Courier New"]/opt/sun/sunstudio12/man[/FONT] to your $MANPATH

---

### Post by .:PiXi²:. on 2009-06-07
This is a great howto, but there's one thing I don't understand.
How do you:
```
add /opt/sun/sunstudio12/bin to your $PATH and /opt/sun/sunstudio12/man to your $MANPATH
```
Thanks in advance!

---

### Post by Filmorependrgn on 2009-09-26
You update your $PATH and [$MANPATH]("http://manpages.ubuntu.com/manpages/karmic/man1/manpath.1.html") are environment variables set by your shell. And where they should be set is dependent on the distribution and the shell of choice. For 90% of the people out there, adding
```

PATH=/opt/sun/sunstudio12/bin:$PATH
MANPATH=/opt/sun/sunstudio12/man:$MANPATH

```
To your ~/.bashrc will work fine.

---

### Post by Filmorependrgn on 2009-09-26
Your $PATH and [$MANPATH]("http://manpages.ubuntu.com/manpages/karmic/man1/manpath.1.html") are environment variables. And where they should be set is dependent on the distribution and the shell of choice. 

For 90% of the people out there, adding
```

PATH=/opt/sun/sunstudio12/bin:$PATH
MANPATH=/opt/sun/sunstudio12/man:$MANPATH

```
To your ~/.bashrc will work fine.

---

### Post by Softwayer on 2010-02-04
Isn't it simplier to download the tarball?

---

### Post by Filmorependrgn on 2010-02-05
> **Softwayer said:**
> Isn't it simplier to download the tarball?

Perhaps. If you write up a response post with a howto on that I'll put it at the top of the thread.

---

