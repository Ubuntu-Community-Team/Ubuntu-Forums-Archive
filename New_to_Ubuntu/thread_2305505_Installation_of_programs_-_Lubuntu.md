---
title: "Installation of programs - Lubuntu"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by LudwigM on 2015-12-06
Hello,
I am new to Linux. I have installed Lubuntu 14 on my laptop.
Now I like to know how I install a program on Lubuntu.
For example I like to install FileZilla. In order to do this I have downloaded a package (.tar.bz2) from the official website ([https://filezilla-project.org/download.php?show_all=1](https://filezilla-project.org/download.php?show_all=1)).
What I have to do with this package now?

Sorry for this really basic question...


Ludwig

---

### Post by maglin2 on 2015-12-06
I don't use it, but Filezilla is in the Ubuntu software centre repositories. Can't you just install it from there using either software centre, synaptic package manager, or via terminal - sudo apt-get install filezilla.

---

### Post by Bashing-om on 2015-12-06
LudwigM; Hello;

While possible to install from a .deb file .. there are much easier ways to install.
This is not Windows where one had to seek and search . We have a software repository of an excess of 43,000 packages.
All available at the click of a button.
The default tool to find stuff in the repository is the "Ubuntu Software Center" utility.
More advanced is ' synaptic'
and even the more advanced is a direct application of 'apt' .. both 'USC and synaptic are frontends for apt ( apt is the package management system built on ' dpkg' ).

Filezilla -> 'apt' shows:
```

sysop@1404mini:~$ apt-cache show filezilla
Package: filezilla
Priority: optional
Section: universe/net
Installed-Size: 3188
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Adrien Cunin <adri2000@ubuntu.com>
Architecture: amd64
Version: 3.7.3-1ubuntu1
<snip>

```

It is in the repo .

[INDENT][INDENT][INDENT]keep'n it simple
[/INDENT][/INDENT][/INDENT]

---

### Post by oldrocker99 on 2015-12-06
Another, and (IMHO) better way is to type this in a terminal:```
sudo apt-get install filezilla
```

You'll be asked for your password, which will **not** show any characters when you type it in.

One of the greatest things about Linux is the ability to install and remove software from the terminal. It's quicker than the Software Center, and even Synaptic.

---

### Post by leunam12 on 2015-12-07
For most of my FTP-ing I use FireFTP which is an add-on for Firefox. That is a pretty simple alternative, it just opens as another tab in Firefox and it allows drag and dropping directly from Nautilus

---

