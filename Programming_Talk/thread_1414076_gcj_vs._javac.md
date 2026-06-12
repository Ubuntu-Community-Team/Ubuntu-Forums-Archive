---
title: "gcj vs. javac"
date: 2010-02-23
forum: Programming Talk
---

### Post by skytreader on 2010-02-23
Just a quick question: what's a better java compiler, gcj or javac? Are there any pros and cons between the two?

---

### Post by CptPicard on 2010-02-23
Sun's Java is the only game in town. I guess you could say that it has all the pros from robustness to API completeness and so on and GNU Java has all the cons... ;)

---

### Post by Queue29 on 2010-02-23
*Oracle's* Java is the only one that should even exist. OpenJDK was made when Java was closed source, which it isn't now, so it's time for the cheap knock off to die. And when I say cheap, I mean check out this real - world example of how the open source clone has rendered Java entries unusable in this contest: 

[http://csclub.uwaterloo.ca/contest/forums/viewtopic.php?f=9&t=201](http://csclub.uwaterloo.ca/contest/forums/viewtopic.php?f=9&t=201)

OpenJDK is slow, incomplete, redundant, and not the official version of the software it imitates.

---

### Post by kahumba on 2010-02-23
Afaik gcj != OpenJDK, though they could have been merged. Gcj has been the Gnu project for ages, while OpenJDK was Sun's open sourced version of their Java + temporary bad code to replace the code that they couldn't open source.

---

### Post by SeanHodges on 2010-02-23
> **Queue29 said:**
> *Oracle's* Java is the only one that should even exist. OpenJDK was made when Java was closed source, which it isn't now, so it's time for the cheap knock off to die. And when I say cheap, I mean check out this real - world example of how the open source clone has rendered Java entries unusable in this contest: 

[http://csclub.uwaterloo.ca/contest/forums/viewtopic.php?f=9&t=201](http://csclub.uwaterloo.ca/contest/forums/viewtopic.php?f=9&t=201)

OpenJDK is slow, incomplete, redundant, and not the official version of the software it imitates.

Correction: **GCJ** was made when Java was closed source.

OpenJDK is Sun's JDK with the non-GPL compatible components removed. [http://en.wikipedia.org/wiki/OpenJDK](http://en.wikipedia.org/wiki/OpenJDK).

In addition: "In July 2009, OpenJDK binary build for Ubuntu 9.04 passed all of the compatibility tests in the Java SE 6 JCK." [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000587.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000587.html)

---

