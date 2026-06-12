---
title: "Creating static packages"
date: 2009-07-07
forum: Packaging and Compiling Programs
---

### Post by mhdbnoimi on 2009-07-07
Hi All,

I want to know how I can create static package (standalone package) just like most MS windows installers?

Static package example:
[http://www.wormux.org/wiki/download.php?/en/](http://www.wormux.org/wiki/download.php?/en/)

---

### Post by kklimonda on 2009-07-08
A static package you download (wormux-0.8.4-static-x86.sh) is in fact a .tar.gz archive with a small wrapper written in sh.
When you execute it the content of archive is unpacked to tmp folder and then a game is launched. This archive contains not only binary and data files (i.e. music and graphics) but also all needed libraries.

You can see for yourself how it looks by doing:
```
cat wormux-0.8.4-static-x86.sh |tail -n +11 |tar xz
```
This command will create a new folder **wormux-0.8.4svn-r** that contains all the files.

Now to create a static package like that all you have to do is prepare required files, compress them and create the small sh wrapper that unpacks it and runs a program. Now, I know that there is a package that prepare such a wrapper but I can't think of its name. But you can use the script that is distributed with wormux. You will get it by doing
```
head -11 wormux-0.8.4-static-x86.sh
```

---

### Post by mhdbnoimi on 2009-07-08
> But you can use the script that is distributed with wormux
I think this is not a practical solution, because there are many packaging tools such as [installjammer](http://installjammer.com/) working like windows installers (actually it's cross-plateforms tool) but most of them don't fix dependecy hell where this problem not exist at all in windows, but I noticed that there are some softwares dealing with this problem in mysteries way like wormux and [QtCreator](http://www.qtsoftware.com/).

I know exactly what wormux-0.8.4-static-x86.sh does, but [color=#FF0000]how they get all dependecies of wormux excutable? this is exactly what I'm looking for in Linux/ubuntu.[/color]

In windows this is not a problem at all, because there is a free tool called [Dependecy Walker](http://www.dependencywalker.com/) can collect whole needed files for specific excutable, where in Linux/ubuntu I cound't find like this tool!!

---

### Post by kklimonda on 2009-07-09
> **mhdbnoimi said:**
> I know exactly what wormux-0.8.4-static-x86.sh does, but [color=#FF0000]how they get all dependecies of wormux excutable? this is exactly what I'm looking for in Linux/ubuntu.[/color]

In windows this is not a problem at all, because there is a free tool called [Dependecy Walker](http://www.dependencywalker.com/) can collect whole needed files for specific excutable, where in Linux/ubuntu I cound't find like this tool!!

You can use ldd binary to get a list of libraries it is linked against.

---

### Post by mhdbnoimi on 2009-07-11
[quote="kklimonda"]You can use ldd binary to get a list of libraries it is linked against.[/quote]
Thanks, this is exactly what I'm looking for, but is there any GUI application for ldd

---

### Post by badeagle on 2009-07-12
You might also be interested in GiftWrap, a .deb package creation wizard. It's brand new and only has basic functionality but I already couldn't live without it.

[http://giftwrap.tuxfamily.org/index.php?](http://giftwrap.tuxfamily.org/index.php?)

---

If no GUI front-end to ldd exists I'll make one.

---

### Post by mhdbnoimi on 2009-07-13
[quote="badeagle"]You might also be interested in GiftWrap, a .deb package creation wizard.[/quote]
Nice, it's a wizard but it can't collect all needed dependencies. Anyway **kklimonda** answered my question clearly but if anyone wants to provide me any gui application just like **ldd** I'll be glad:lolflag:.

Thanks all:p

---

