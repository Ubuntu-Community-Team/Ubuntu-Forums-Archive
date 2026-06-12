---
title: "Where can I view the source code of the programs Ive downloaded?"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by bach80 on 2013-02-04
:pHello all:p

I recently installed ubuntu partly because I want to view the source code of the programs I downloaded.

Funny thing ... I can't find the the programs ... I don't know where they are.

I found the executable to one of the games (Flare) in usr/games, but that is only an executable which doesn't show me any code if opened in notepad.

Can someone lead me to the correct directory that will show all the files that make up this game?

And once I do find them,  do I just open them with some type of text editor? 

Thank you for your time.

---

### Post by MG&amp;TL on 2013-02-04
There's various ways of getting source code. Ubuntu doesn't provide source code by default; for most users it's just useless text files.
 
If you downloaded something from the repositories, you can dump the source code (of the exact version you downloaded) with:
 
```
apt-get source <package>
```
 
where <package> is, for example, *inkscape*.
 
Another way is by direct download: many developers also distribute their programs as *source tarballs* - that is, they provide compressed source code downloads. (They're called tarballs as the compression used is usually a combination of *tar* and *gzip*).
 
If you really like to keep abreast of developments, most software uses *version control* to keep track of changes and centralise development. Examples of version control software include *bazaar *(what Ubuntu uses), *git* (popular-written by Torvalds!), *subversion, *and *mercurial*. Explaining how to use these is a futile process- if the developer offers this method, then I suggest reading a quick tutorial on the version control software in question. 
 
Happy coding!

---

### Post by Paqman on 2013-02-04
Just to clarify things a bit more: normally when you download a package on an Ubuntu system you don't get source code. You get a precompiled binary package. On Debian-based systems such as Ubuntu that will be a .deb file, which unpacks itself onto your system when installed. The package manager doesn't download source and compile it on your system, the .debs are all precompiled by Ubuntu's build servers before being added to the repos.

You can download the source code for any package in the ways MG&TL describes.

---

### Post by grahammechanical on 2013-02-04
Do we not have to activate a setting in Software Sources to get source code as part of the download?

---

### Post by Paqman on 2013-02-04
IIRC the source repos are enabled by default. I know this because I usually go in and switch them off on a new install to speed up my repo updates.

---

### Post by MG&amp;TL on 2013-02-04
> **grahammechanical said:**
> Do we not have to activate a setting in Software Sources to get source code as part of the download?
 
I could be wrong, but I think that just enables you to download source code, it doesn't actually automate the process...?

---

### Post by jerome1232 on 2013-02-04
> **MG&TL said:**
> I could be wrong, but I think that just enables you to download source code, it doesn't actually automate the process...?

But when you check for updates, it checks those repositories, by disabling them he avoids checking the unused repositories and speeds up the process of checking for updates.

---

### Post by Paqman on 2013-02-04
> **MG&TL said:**
> I could be wrong, but I think that just enables you to download source code, it doesn't actually automate the process...?

Correct. If you want the source you have to ask the package manager for it specifically.

---

