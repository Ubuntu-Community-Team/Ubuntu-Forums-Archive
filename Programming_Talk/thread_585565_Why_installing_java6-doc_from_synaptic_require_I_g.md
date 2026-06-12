---
title: "Why installing java6-doc from synaptic require I go to sun download page?"
date: 2007-10-21
forum: Programming Talk
---

### Post by hecato on 2007-10-21
Here is what synaptic console output...
> 
This package is an installer package, it does not actually contain the
JDK documentation. You will need to download one of the archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the not update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and then copied to /tmp

[Press RETURN to try again, 'no' + RETURN to abort]


---

### Post by tenmillionmilesaway on 2007-10-21
becaue the javadoc isnt in the ubuntu repo.  suppose its cos it isnt strickly a program.  Do as it says i.e. download from sun, chown to root and mv to /tmp then run the install again.

---

### Post by hecato on 2007-10-21
Why the install dont try to wget it (thought you first need to say yes to download...), and print the output of accept the license before download or some like that...

I mean when you install the java sun version, they request a "click on OK".


That will be the preferred way.

In the other case, you simply can go download and put it on any place you want without need to notice that is not possible to install it in synaptic.

------
Also for the point of "not being a program" there a lots of things that are not a programm in the repos, like the "dev files" ie "*.h" and things like that, there is also docs and manuals in the repos.

Also IIRC sometime ago in he 64bit version there was a package related to EAGLE program but was the -data version, but the point is that there where no EAGLE version for 64 bit versions, thus a package that was only there without real use for 64biters in the repo.

---

