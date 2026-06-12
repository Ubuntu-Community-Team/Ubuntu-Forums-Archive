---
title: "Removing files thrown out by netbeans 5.5 installer."
date: 2007-05-18
forum: Programming Talk
---

### Post by Levander on 2007-05-18
I *always* use aptitude to install applications I allow to place files in /usr, /etc, or other hard to find places.  I want to be able to delete the software if I decide I want to manually install a different version of it later (which I *always* do in /opt).  However, this time, me not thinking at all, just really tired and have gotten used to trusting aptitude, I'm prompted to download an install file from the internet.  Lord knows why I did that.  Is there any easy way to get through and remove all those files?  I can't imagine that "aptitude remove" will do it.  

If Ubuntu's going to make some package to download a bunch of dependencies, and then tell you where to go download it yourself, I think they're trying to overdo the ease of use thing.  I assume the package is there to make sure you install the correct dependencies for netbeans.  But really, what's the point of them going the next step and telling you where to download it from? Then having aptitude just run their installer, when aptitude won't even manage the files that are installed.  That's been the traditional use of apt, management of files on your system.  Having apt throw out a whole slew of files that it won't manage really kind of defeats the purpose.  The package doesn't have to run the netbeans installer, it could just give you a link telling you where to download it from, then have you install it yourself.  Not quite as easy, but doesn't completely cut around the idea that files installed with aptitude are managed by aptitude, like the current solution does.

Anway, anyone know how to remove all these files the netbeans installer threw out there?

---

### Post by Levander on 2007-05-18
Perhaps I posted too soon.  "for i in `tar tzf netbeans-5_5.tar.gz` ; do ls -l $i ; done 2> /dev/null"  has not output.  So, perhaps the netbeans 5.5 package does let aptitude manage the files that you have to download from netbeans.info?

---

