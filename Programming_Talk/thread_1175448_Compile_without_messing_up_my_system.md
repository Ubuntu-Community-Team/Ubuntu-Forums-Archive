---
title: "Compile without messing up my system?"
date: 2009-06-01
forum: Programming Talk
---

### Post by nwarrenfl on 2009-06-01
Hello everybody!

I have a few projects and contributions, and something i dislike is that i must install a lot of packages (libs) to be able to compile programs, and i don't like that.

Is there a way, i think i must use fakeroot, to make a fake system in my Ubuntu installation to install packages on it and compile my programs?

So i could keep my system clean with no tons of packages i do not need for a normal system...

Thanks in advance!

---

### Post by simeon87 on 2009-06-01
I wouldn't know how to do that but are the packages really that much of a problem? All they do is taking up some disk space..

---

### Post by nwarrenfl on 2009-06-01
Well there is a huge amount, Wine for example needs a lot of packages...

---

### Post by MadCow108 on 2009-06-01
a virtual machine would be a solution.

or you just save all the names of the installed packages and purge them again when your finished.

---

### Post by nwarrenfl on 2009-06-01
Yes, i tought it would be ideal to make a virtual machine, but i would like something "native"...

Any solution?

---

### Post by ajackson on 2009-06-01
If something needs a specific library it needs it and uses it, if something doesn't need that library the chances of that library screwing it up if present are virtually zero.

---

### Post by nvteighen on 2009-06-01
Er... it's funny: your system is not a "normal" system if you're using it for development... it's a development platform, so you need development packages... What can be wrong with that? :)

For you to calm down: development packages (*-dev) will usually just install headers, which are harmless, and static libraries (.a... not really different to a .tar file). Sometimes they include documentation... Nothing of that can mess your system, as they're non-executable and nothing will access them at runtime (as opposed to shared libs). So don't worry.

---

### Post by SledgeHammer_999 on 2009-06-01
> **nwarrenfl said:**
> Hello everybody!

I have a few projects and contributions, and something i dislike is that i must install a lot of packages (libs) to be able to compile programs, and i don't like that.

Is there a way, i think i must use fakeroot, to make a fake system in my Ubuntu installation to install packages on it and compile my programs?

So i could keep my system clean with no tons of packages i do not need for a normal system...

Thanks in advance!

I am interested too. And I think this is possible to do. I remember something like that in a tutorial on how to package programs(make debs). The thing is, I don't remember where I read about it. :S

---

### Post by SledgeHammer_999 on 2009-06-01
I was intrigued by your question and I did a little search. I think I found a suitable answer here: [ubuntu packaging wiki](http://wiki.ubuntu.com/PackagingGuide/Complete#The%20Personal%20Builder:%20pbuilder)
I think **pbuilder** is the right thing for you:
> Using pbuilder as a package builder allows you to build the package from within a chroot environment. You can build binary packages without using pbuilder, but you must have all the build dependencies installed on your system first. However, pbuilder allows the packager to check the build dependencies because the package is built within a minimal Ubuntu installation, and the build dependencies are downloaded according to the debian/control file.

---

### Post by nwarrenfl on 2009-06-01
I know it doesn't harm, i just want to not have all those packages installed and listed in Synaptic...
But pbuilder is only to build packages, or not?

---

### Post by ajackson on 2009-06-01
> **nwarrenfl said:**
> I know it doesn't harm, i just want to not have all those packages installed and listed in Synaptic...
You'll find it hard to develop without them.

---

