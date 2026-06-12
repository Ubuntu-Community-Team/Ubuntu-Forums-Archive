---
title: "skype Error: Wrong Architecture 'i386'"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-29
I have installed the 64 bit version of Ubuntu on my computer with an AMD Turion Processor.  Perhaps I should have installed the 32 bit because when I try to install skype I get the following error.

skype Error: Wrong Architecture 'i386'

Any suggestions?

---

### Post by P3ngu1n0 on 2008-05-29
get a 64 bit version of skype, check the skype repos or "sudo apt-get install skype" in terminal (no qoutes)

---

### Post by Joeb454 on 2008-05-29
I think skype is in the medibuntu repo's.

And you could use the -force option, but I have no idea how it works etc.

---

### Post by sayakb on 2008-05-29
```
sudo dpkg -i --force-architecture packagename.deb
```
Try installing like this. Works fine in most cases :)

---

### Post by Golem XIV on 2008-05-29
The problem is that you're trying to install a package compiled for a 32-bit system on a 64-bit system.

There is no 64-bit Skype package, but it is possible to install 32-bit packages on 64-bit systems by first installing ia32-libs.

Here is a [guide on how to install Skype on a 64-bit system]("http://ubuntuforums.org/showthread.php?t=432295").

---

### Post by RamT on 2009-02-08
I have had this come up too.  I just got a Sylvania meso netpad.  See link [http://www.sylvaniacomputers.com/products.php?p=meso](http://www.sylvaniacomputers.com/products.php?p=meso) and it has a intel Atom Processor on it.  I dont' know if this is a 32bit proecessor or a 64 bit processor with Ubuntu 8.04.1 installed on it.  

Anyway I don't know the first thing about it but when I trieed to install both skype and Gizmo on it I got this message.  I just double clikcked the deb file. 

I don't know much about Ubuntu or programming but thought it would be nice to get away from windows, but I am not sure if it is worth it.  Anybody got some sound advice about what I can do before I defect back to the default???

I would appreciate it.

---

