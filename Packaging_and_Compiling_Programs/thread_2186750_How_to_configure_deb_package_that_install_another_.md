---
title: "How to configure deb package that install another package"
date: 2013-11-08
forum: Packaging and Compiling Programs
---

### Post by dentaku65 on 2013-11-08
Hi,

sorry for the silly question, but I have a question about deb packaging.
I've created correctly my package, but I do not understand how to install another package when I intall the one that I have buildt.

What I expect is the when I'm install my package, the installation will provide to install a dependent package (curl in this case)

This is my control file:
> Source: mypublic
Section: utils
Priority: extra
Maintainer: dentaku65 (dentaku for ubuntu) <dentaku65@xxxx>
Build-Depends: debhelper (>= 8.0.0)
Standards-Version: 0.1-20
Homepage: <insert the upstream URL, if relevant>

Package: mypublic
Architecture: any
Depends: [COLOR="#FF0000"]curl[/COLOR]
Description: mypublic
 mypublic

I don't know how to build my deb that when is installed, will install curl too.

TIA

---

### Post by ian-weisser on 2013-11-08
A rather handy explanation was in the Debian User Forums. See [http://forums.debian.net/viewtopic.php?f=19&t=77053](http://forums.debian.net/viewtopic.php?f=19&t=77053)

The short answer is that is may depend upon how you are compiling (or creating) the package.
The longer answer is that you put the dependency in the right place in the control file.

Is the package not building?
Is the package not installing?
Is the dependency not installing?
Are you getting any error messages?

---

### Post by dentaku65 on 2013-11-09
Hi ian,

thank you for your answer; the package was correct, but I did not know that dpkg is ignoring *Depends* entry; in fact doing:
```
sudo dpkg -i <pkg.deb>
```
give me the output with curl as missing package

So I've upload my package on PPA and with the:
```
sudo apt-get install <pkg.deb>
```
Correctly install curl with my package.

I did not know that dpkg and apt (and aptitude) have different behaviour on installing a deb package.

den

---

### Post by ian-weisser on 2013-11-09
I'm happy to see that it's working for you now.

---

