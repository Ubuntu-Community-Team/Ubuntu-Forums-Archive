---
title: "KDE 3.5 Headers"
date: 2006-01-04
forum: Packaging and Compiling Programs
---

### Post by Brando569 on 2006-01-04
ive searched through the forums and couldnt find an answer to my problem. im running KDE 3.5 and want to install something that needs the development files for it (libs and headers) but i dont know where to get them, the ones in the repository are for 3.4.3, ive tried to install then but they wont work. where can i get the dev files for 3.5? thanks.

---

### Post by pjman on 2006-01-13
I am looking for this as well.

---

### Post by madtinkerer on 2006-01-14
bump

---

### Post by madtinkerer on 2006-01-14
I installed libkde4-dev and it seems to have installed all the required headers and libs.

---

### Post by asimon on 2006-01-14
Which repository do you use for KDE 3.5? The [Kubuntu packages for KDE 3.5](http://kubuntu.org/announcements/kde-35.php)? Looking at this [repo](http://kubuntu.org/packages/kde35/pool-breezy/) shows that it contains all those *-dev files which you need.

Oops: Saw your last message too late.
If you don't know what packages to install, the headers are all distributed in those -dev files, for example libkde4-dev contains all headers for the kdelibs. kdebase-dev contains the headers of kdebase and so on. A nice way to install -dev packages is via command line with something like
```
$ apt-get build-dep kdepim
```
That command would install all packages which you need to build kdepim from source. Of course this only works for packages which are already in the repository.

---

