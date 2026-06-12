---
title: "snaptic pakage manager isn't finding archives"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by ajlinzey on 2008-09-12
I'm trying to load a program (eclipse-cdt) and after I click apply I get the following error
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-jdt_3.2.1-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-jdt_3.2.1-0ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]
 I tried reloading the archive indexes and a slew of them couldn't be downloaded as well.
thanks
-Andy

---

### Post by t0p on 2008-09-12
Do you definitely have internet access on the computer?  Sounds like it isn't connecting to the net to me...

---

### Post by ajlinzey on 2008-09-13
I'm using the internet connection on that computer to make these posts.
-Andy

---

### Post by Mornedhel on 2008-09-13
Try changing your repositories ?

I use [http://archive.ubuntu.com/etc](http://archive.ubuntu.com/etc)... (note absence of the us. at the beginning).

Sometimes repositories just go offline.

---

### Post by ajlinzey on 2008-09-14
I tried changing the repository from US to ma[CENTER][FONT="Arial Black"]in and hit reload and got
could not down load all repository indexes with the following list (and eclipse-cdt isn't an available package)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:) 404 Not Found
thanks 
-Andy

---

