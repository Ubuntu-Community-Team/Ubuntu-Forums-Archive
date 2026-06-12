---
title: "leJOS installation troubles with 'make' and 'ant' on Edgy"
date: 2006-11-05
forum: Programming Talk
---

### Post by isaacf on 2006-11-05
I'm working with leJOS for school and trying to install version 2.1.0 on my home computer.

I've followed the instructions here:
[http://lejos.sourceforge.net/tutorial/getstarted/firstbrick/linux.html](http://lejos.sourceforge.net/tutorial/getstarted/firstbrick/linux.html)

but when I run 'ant' to build it, it tells me build.xml does not exist so I ran 'make' which I saw here:
[http://lejos.sourceforge.net/installunix.html](http://lejos.sourceforge.net/installunix.html)

but it tells me that: 

"javac: target release 1.1 conflicts with default source release 1.5
make: *** [core_classes] Error 2"

does this mean I need to install version 1.1 of the SDK? The site told me 1.5 would work.

---

### Post by hod139 on 2006-11-21
Are you sure you are running Sun's java?  If you type java -version what do you see.

---

