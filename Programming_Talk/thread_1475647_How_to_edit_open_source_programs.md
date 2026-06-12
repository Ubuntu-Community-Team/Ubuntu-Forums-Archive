---
title: "How to edit open source programs"
date: 2010-05-07
forum: Programming Talk
---

### Post by Experimental on 2010-05-07
Are there any tutorials here showing how to edit a program installed in ubuntu ? I know C/C++ and I want to try to use this knowledge to edit some open source programs

---

### Post by loell on 2010-05-07
thread moved to Programming Talk.

---

### Post by 3rdalbum on 2010-05-07
Sudo apt-get source (packagename)

Puts the source code folder into the current working directory.

---

### Post by nvteighen on 2010-05-07
> **3rdalbum said:**
> Sudo apt-get source (packagename)

Puts the source code folder into the current working directory.

**Don't use sudo** or you'll end up giving ownership to root of a bunch of files copied into some part of your /home directory... , Ok, it won't harm your system, but it's just unconvenient (you'll have to chown the files later) and unnecessary. Usually is a bad idea to use sudo where unneeded.

Just use:
```

apt-get source whatever-package

```

Be careful that everuthing will be just downloaded directly onto the current directory, so better create a new directory for this, change into it and then do the apt-get source.

---

### Post by Bachstelze on 2010-05-07
> **3rdalbum said:**
> Sudo apt-get source (packagename)

Do **not** use [font=monospace]sudo[/font] with [font=monospace]apt-get source[/font]. [font=monospace]apt-get source[/font] downloads and unpacks the source in the current directory. If you run it with [font=monospace]sudo[/font], all your source tree will be owned by root, which means you will have to do all your work as root, which is silly.

*EDIT: hey, nvteighen!*

---

### Post by diesch on 2010-05-07
```
sudo apt-get build-dep packagename
```

installs you everything else you nedd to build package *packagename*

---

### Post by Diabolis on 2010-05-08
Some times the packages in the repo are not the newest version, so it might be a good idea to go directly to the page of the project and get the source code from it.

---

### Post by phrostbyte on 2010-05-09
First as others have said

```
apt-get source package
```

spits out the source code in the current working directory

Next, modify the program in any which way you want.

Then ...

```
sudo apt-get build-dep package
dpkg-buildpackage

```

This will create a .deb from your modified application, which you can then double click or use dpkg -i to install.

If you want to be a little cleaner, modify the fields of the debian/control file in the source code to differentiate it from the original package (ie. change debian version number).

---

