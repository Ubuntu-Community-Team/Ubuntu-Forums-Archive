---
title: "help!"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by cold37 on 2008-05-17
i try to go in to my Synaptic Package Manager and all i see is --> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 <--- how can i fix it pls

---

### Post by adult swim on 2008-05-17
go to applications/accessories/terminal and type in ```
sudo dpkg --configure -a
``` then hit enter, it will ask for your password so type that in and hit enter and your problem should go away.

---

### Post by ramjet_1953 on 2008-05-17
OK, you just do what it is telling you.

open a terminal and type in what it says. ie

[COLOR="Red"]sudo dpkg --configure -a[/COLOR]

Regards,
Roger :cool:

---

### Post by empthollow on 2008-05-18
another thing to try that may also solve your problem and is sometimes quicker is:
```
sudo apt-get -f install
```
this must be done in a terminal with synaptic closed.

---

### Post by Matt640 on 2008-05-24
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

