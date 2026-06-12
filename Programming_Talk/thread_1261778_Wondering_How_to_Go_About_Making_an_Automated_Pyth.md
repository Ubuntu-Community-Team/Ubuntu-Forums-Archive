---
title: "Wondering How to Go About Making an Automated Python Script"
date: 2009-09-09
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-09-09
Ey guys, I have been working on a python script to backup files for developers. It is working the way it should, but I would like to make it automated so that whenever a certain percentage of the file that is being monitored changes, it automatically creates a backup of that file. I was wondering how to go about doing this and all I could really think of was having the script check the file every x time units to see how much it had been modified. This is not ideal though since this constant polling of the file will waste resources especially if the computer is idle and the file is not being worked on. 

So I was wondering is there any way I can make it so that I don't have to constantly check the file? Are there any system functions that can help me with this? Thanks in advance.

---

### Post by haTem on 2009-09-09
You should look into inotify. It provides a mechanism for monitoring the filesystem for changes, and I believe it has python bindings.

[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)
[http://pyinotify.sourceforge.net/](http://pyinotify.sourceforge.net/)

---

### Post by StunnerAlpha on 2009-09-10
> **haTem said:**
> You should look into inotify. It provides a mechanism for monitoring the filesystem for changes, and I believe it has python bindings.

[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)
[http://pyinotify.sourceforge.net/](http://pyinotify.sourceforge.net/)
Sick man, thanks! Just what I was looking for!

---

### Post by StunnerAlpha on 2009-09-28
I looked more into inotify and realized that it only works for Linux platforms, not on the Mac OS X platform. Is there any other utility similar to this that can let my script know when a file is modified that will work for all flavors of unix?

And a part 2 to my question, if I were to install and use inotify and develop the script for Linux OSes only how would I make it so that people can simply dl my script and then run an install command and have everything the script needs installed automatically? I have been trying to look this up on google and the closest I came was launchpad's Ubuntu installer. Is there anything I should read to learn more about making my script easily installable?

Thanks in advance.

---

### Post by unutbu on 2009-09-28
Perhaps make it into an Ubuntu package: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete). This solves the dependency issue by using the dpkg system. Of course, that would only help people using Ubuntu and maybe other dpkg-based systems. If you'd like it to work with other Linux OS's, you'd have to also package it as an RPM, and tar.bz2...

I think you are right that python-pyinotify only works with Linux because it relies on Linux kernel inotify syscalls.

---

### Post by StunnerAlpha on 2009-09-28
> **unutbu said:**
> Perhaps make it into an Ubuntu package: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete). This solves the dependency issue by using the dpkg system. Of course, that would only help people using Ubuntu and maybe other dpkg-based systems. If you'd like it to work with other Linux OS's, you'd have to also package it as an RPM, and tar.bz2...

I think you are right that python-pyinotify only works with Linux because it relies on Linux kernel inotify syscalls.

Thanks for the response. Yeah inotify doesnt work with mac for sure since I tried installing it on my Mac and it refused to do so... :(

---

### Post by StunnerAlpha on 2009-09-28
By the way does anyone know if the functionality in inotify can be found in python version 3?

---

