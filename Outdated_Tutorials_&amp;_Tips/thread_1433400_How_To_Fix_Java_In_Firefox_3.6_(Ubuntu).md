---
title: "How To: Fix Java In Firefox 3.6 (Ubuntu)"
date: 2010-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dreamsburnred on 2010-03-19
When you install Firefox 3.6 from the stable release on Ubuntu 9.10, you will find out that Firefox has no clue where java is. Assuming its is installed run:

For i386 (32 bit Ubuntu):
 ```
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
``` For amd64 (64 bit Ubuntu):
 ```
$ sudo update-alternatives --install  /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50
```[Source]("http://www.nowhere.dk/articles/ubuntu-fixing-java-in-firefox-3-6") (where I found it). :popcorn:

---

