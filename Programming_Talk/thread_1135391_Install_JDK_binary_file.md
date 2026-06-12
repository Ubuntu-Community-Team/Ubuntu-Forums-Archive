---
title: "Install JDK binary file"
date: 2009-04-24
forum: Programming Talk
---

### Post by nmccrina on 2009-04-24
Hello all,

This isn't a really critical question, I've installed the jdk binary many times (every time I reinstall Ubuntu, which is dozens, lol) and it works. I was wondering, however, what the difference was between the 'java' and 'javaws' programs in jdk-<version>/bin and jdk-<version>/jre/bin (if any)? Does it matter which ones I symlink to from /usr/local/bin? Is the jre version of 'javaws' less suitable for developing?

Thanks!

---

### Post by jespdj on 2009-04-26
'javaws' is for [Java Web Start](http://en.wikipedia.org/wiki/Java_Web_Start), while 'java' is the normal Java program launcher.

I don't know what you mean exactly by "installing the JDK binary file", but you can just install the JDK from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```
That's easier than downloading it from Sun's website and installing it manually.

---

### Post by doorman on 2009-04-26
It actually doesn't matter which one you symlink if their versions are equal (the binaries are the same).

The reason you have multiple binaries is because both jdk are jre get installed when installing jdk. There's a simple explanation for this: all java applications require jre to run, while the development process requires the jdk (which is a superset of the jre)

---

