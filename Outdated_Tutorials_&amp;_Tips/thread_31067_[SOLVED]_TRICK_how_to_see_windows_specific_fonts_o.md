---
title: "[SOLVED] TRICK: how to see windows specific fonts on your webpages"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-05-01
This is a small trick that will make some webpages on your browsers appear as smooth and well aligned as they do on windows .

go to terminal and type

sudo apt-get install msttcorefonts

thats it! look at the remarkable difference in your browser after you install this windows font package. For example check out [www.rediff.com](www.rediff.com) before and after you install the above package.

---

### Post by seven on 2005-05-01
ah, thanks. 
but there are a few HOWTOS about this in the forum allready

---

### Post by arnieboy on 2005-05-01
doesnt matter! sometimes u wud want to share your words of wisdom irrespective of whether they have already been spoken. They will invariably be taken notice of and will be appreciated.

---

### Post by punkinside on 2005-05-01
```
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```

what rep is it in!?

---

### Post by 23meg on 2005-05-01
it's in universe.

---

### Post by flightcrank on 2005-05-03
[QUOTE=23meg]it's in universe.[/QUOTE]
 i get the same issue as punkinside, and i hae the universe repo

---

### Post by arnieboy on 2005-05-03
please make sure your /etc/apt/sources.list looks like  the one below if u are using hoary. These contain almost all repositories u need for hoary. add whatever u feel is missing.

#START

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#END

---

### Post by Nis on 2005-05-03
> 
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

Be careful when using Marillat.  Without proper pinning you can seriously screw up your system.  Most things in Marillat are in Ubuntu backports anyway so the usefullness of Marillat on Ubuntu is decreasing.

---

### Post by cuoog on 2005-05-08
has anyone else installed msttcorefonts and had it break java?  all java applets just sort of sit there and dont open, just showing the java logo.  was working fine before this.  This is with sun java 1.4.2, btw, i'm gonna try upgrading to 1.5.  any ideas on what might of caused this and how to fix it?

much appreciated...

db

---

### Post by dikki on 2005-05-30
I didn't have any problems with java after installing msttcorefonts. Btw I use 1.5.03, but I don't think 1.4.2 would be wrong, neither.

---

### Post by CzarDerivative on 2005-06-05
[QUOTE=23meg]it's in universe.[/QUOTE]

Actually, the msttcorefonts package is in multiverse.

---

