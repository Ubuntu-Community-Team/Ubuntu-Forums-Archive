---
title: "[SOLVED] Errors with java -- should I install new version?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-10
Through Synaptic Package Manager, I have installed

[LIST]
[*] sun-java6-bin
[*] sun-java6-fonts
[*] sun-java6-jre
[*] sun-java6-plugin
[/LIST]
 (These are all version 6-06-0ubuntu1.)

I'm getting an error when running a specific Java program:
> com.sun.star.lib.loader.Loader::getCustomLoader: cannot add UNO jar files: java.lang.ClassNotFoundException: com.sun.star.comp.helper.UnoInfoAccording to [www.java.com]("http://www.java.com"), there is a newer version (version 6 update 7).

Is it worth updating Java (I don't quite understand the instructions to do so), or is something else causing the error?

---

### Post by Paddy Landau on 2008-07-10
I answered my own question after a chance discovery.

The java program in question accesses OpenOffice.

I needed to install
openoffice.org-java-common
(available through Synaptic Package Manager).

---

