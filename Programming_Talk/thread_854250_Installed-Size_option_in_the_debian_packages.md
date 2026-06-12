---
title: "Installed-Size option in the debian packages"
date: 2008-07-09
forum: Programming Talk
---

### Post by Paretje on 2008-07-09
Look, this is the control file of the firefox-package in Ubuntu:
```
Package: firefox
Source: firefox-3.0
Version: 3.0~b5+nobinonly-0ubuntu3
Architecture: all
Maintainer: Alexander Sack <asac@ubuntu.com>
Installed-Size: 120
Depends: firefox-3.0
Section: web
Priority: optional
Description: meta package for the popular mozilla web browser
 Firefox 3 is the next major release of the standalone Mozilla browser; it is
 written in the XUL language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firefox 2, Firebird and Phoenix.
 .
 This is a meta package that will point to the latest firefox package in ubuntu.
 Don't remove this if you want to receive automatic major version upgrades for
 this package in future.
```

Everything is clear, except one thing: Installed-Size. What do I have to fill in there exactly AND how can I get that.

---

### Post by Paretje on 2008-07-24
Nobody?

---

### Post by bobbocanfly on 2008-07-24
You will want to ask the Maintainer Alexander Sack on IRC about it probably, he will be able to tell you.

He idles in #ubuntu-mozilla-team (or something similar) and has the nickname 'asac'.

---

### Post by Paretje on 2008-07-24
Well, in fact this is only an example of a package. I want to make a package, but I don't know what I have to enter for that.

---

### Post by maybeway36 on 2008-08-18
Installed-Size is the total size in kilobytes of all the files in the package.
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Installed-Size]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Installed-Size")

---

### Post by Paretje on 2008-08-18
Is there a commad to get that information?

---

### Post by maybeway36 on 2008-08-19
To be honest, I'm not sure. I usually just open Konqueror, right-click, and look at the properties. That might not be totally accurate, though.

---

### Post by Paretje on 2008-08-19
With Konquerror you get that information? Under nautilus, it's the shortest notation, which means for example 9,4MB

---

### Post by spikyjt on 2008-08-21
On the command line:
```
du -sx --exclude DEBIAN package-dirname
```
(where package-dirname is the name of the folder your package files are in)

I am currently writing a script to easily automate the process of creating deb packages as it seems to be a bit of an art form! Of course if anyone knows of a suitable tool that's already about I'd be most interested. I could only find stuff for building source packages. If you're interested in my script, I can post it when I have completed it. I will also release a package of it, when I have written the GUI.

---

### Post by Paretje on 2008-08-21
Yes, that's it.

When I unpack the simutrans-pak64 package and use that commando, I get this:
```

kevin@kevin-desktop:~$ du -sx --exclude DEBIAN /home/kevin/Desktop/Documenten/Simutrans/100.0/simutrans-pak64_100.0-1_all
11844	/home/kevin/Desktop/Documenten/Simutrans/100.0/simutrans-pak64_100.0-1_all

```

When I look to the value said in the package, it's 11836. A diffrence of 8. I think that acceptable.

Or have you a comment that explains why I have a difrrence?

Anyway: Thanks ;)

---

### Post by dribeas on 2008-08-21
> **Paretje said:**
> Or have you a comment that explains why I have a difrrence?

du outputs the used size in the disk, not the sum of the sizes of the files. It includes the directory where you ask it to compute the size, which will not be part of the tar...

```

$ mkdir test
$ du -sx test
4       test

```

Note that directories take 4K in my system but may be different in your case, you can test it with:

```

$ ls -ld test
drwxr-xr-x 2 dibeas dibeas 4096 2008-08-21 23:58 test

```

In my case du will always sum 4K extra.

---

### Post by Paretje on 2008-08-21
I have indeed in the first one 2 and with the second one 4.

You mean the installed size is without the directories then? Or is it just because they counted not from the root, but from it realy starts (more then just one directory, but two.

It's because when I start from /usr/share, where you have doc and games (two, not just one). I have 11836, just like said in the file.

Is that the real method to do? Not counting the directories which just contains just one follow directory? Or it doesn't matter?

---

