---
title: "libmotif3 is replaced by libmotif4"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by siddhanta on 2011-09-29
hi,
am using ubuntu11.04. and am trying to install libmotif3
[PHP]siddhanta@siddhanta:~$ sudo apt-get install libmotif3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmotif3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmotif4

E: Package 'libmotif3' has no installation candidate

[/PHP]


i google a lot but unable to find any solution. 
so,please, help me to get rid of this issue.

---

### Post by Daveth on 2011-09-29
copy here

[http://packages.debian.org/lenny/libmotif3](http://packages.debian.org/lenny/libmotif3)

---

### Post by siddhanta on 2011-09-29
can u please elaborate what to do after going to this site.
i already downloaded the libmotif3 i386 package but dont know what to do next...

---

### Post by Daveth on 2011-10-07
go to the i386 option at the bottom of the page (assuming that is your PC architecture), click it and that takes you to a set of mirrors holding the .deb file. Find a suitable mirror from which to download the .deb file to your machine, then right click the .deb file to properties and "allow execution", then right click the file and open with Gdebi package installer. That should then give you your missing libmotif file.

---

