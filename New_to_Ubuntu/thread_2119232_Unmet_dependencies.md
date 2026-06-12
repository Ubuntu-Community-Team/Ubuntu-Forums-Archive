---
title: "Unmet dependencies"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by rengglian on 2013-02-23
Hi everybody, 
I did a mistake today and tried to install octave 3.6.2
the 3.2.x version had unsatisfied plot options...

Even the Ubuntu Software Center told me that "Dependency is not satisfiable: libblas3|libblas.so.3|libatlas3-base", I tried to get it running.

```
sudo dpkg -i octave_3.6.3-2_amd64.deb
```
there I got a list of dependency problems that prevent the configuration of octave.
Like:
```
octave depends on libarpack2 (>= 2.1); however:
  Package libarpack2 is not installed
```

Well, I thought that shouldn't be a problem. Let's install those dependencies. 
[LIST]
[*]libamd2.2.0
[*]libarpack2
[*]libblas3
[*]libgfortan3
[*]libc6-udeb_2.17
[*]libc6_2.17
[/LIST]

However, this wasn't a good idea. ( I could have guessed it because the Ubuntu Software Center warned me)
Octave, Ubuntu Software Center and Software Update doesn't work anymore.

```
 sudo apt-get -f install
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.16) but 2.17-0ubuntu4 is installed
 libc6 : Breaks: libc6:i386 (!= 2.17-0ubuntu4) but 2.15-0ubuntu10 is installed
 libc6:i386 : Depends: libc-bin:i386 (= 2.15-0ubuntu10)
              Breaks: libc6 (!= 2.15-0ubuntu10) but 2.17-0ubuntu4 is installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10) but 2.17-0ubuntu4 is installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10)
 libnih1 : PreDepends: libc6 (< 2.16) but 2.17-0ubuntu4 is installed
 octave : Depends: libarpack2 (>= 2.1) but it is not installed
          Depends: libblas3 but it is not installable or
                   libblas.so.3 but it is not installable or
                   libatlas3-base but it is not installable
          Depends: libccolamd2.7.1 (>= 1:3.4.0) but it is not installed
          Depends: libcholmod1.7.1 (>= 1:3.4.0) but it is not installed
          Depends: libcolamd2.7.1 (>= 1:3.4.0) but it is not installed
          Depends: libcxsparse2.2.3 (>= 1:3.4.0) but it is not installed
          Depends: libfftw3-double3 but it is not installable
          Depends: libfftw3-single3 but it is not installable
          Depends: libfltk1.1 (>= 1.1.7) but it is not installed
          Depends: libglpk0 (>= 4.30) but it is not installed
          Depends: libgraphicsmagick++3 but it is not installed
          Depends: libgraphicsmagick3 (>= 1.3.5) but it is not installed
          Depends: liblapack3 but it is not installable or
                   liblapack.so.3 but it is not installable or
                   libatlas3-base but it is not installable
          Depends: liboctave1 (>= 3.6.2) but it is not installed
          Depends: libqhull5 (>= 2003.1) but it is not installed
          Depends: texinfo
          Depends: octave-common (= 3.6.3-2) but it is not installed
          Recommends: libatlas3-base but it is not installable or
                      libopenblas-base but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

```
ldd -version
```
```
ldd (Ubuntu EGLIBC 2.15-0ubuntu10.3) 2.15
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.

```

Is there a quick fix for my problem? or do I have to install Ubuntu again?

What I did so far:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get autoremove
sudo apt-get remove/install libc*

```
and some other google related trail and error commands...(probably a mistake as well)

I would be very grateful for any ideas.
If you need anymore information, just let me know...

Best wishes

---

### Post by rengglian on 2013-02-24
Well, after some playing around, I broke my system completely but could recover (fresh installation without formatting) it with a live CD.
Lesson learned: Don't ignore warnings...
at least no data lost

Best wishes

---

### Post by tgalati4 on 2013-02-24
You have adequately described *Dependency File Hell*.  It's a common problem when trying to install something that is not compiled for your version of linux.  Sometimes you can install newer libraries alongside older libraries and get newer packages to work.  But not always.  

Usually it's pretty easy to recover from apt errors, but it sounds like your system got balled up tight.  Next time look in /var/log/apt and post some output so we can better assist what is going on.  It's also helpful to look at the dependencies side-by-side so you can see how many libraries need to be changed:

```
apt-cache depends octave
```

As you can see, it uses a lot of shared libraries.  Did the 3.2 version not work out-of-the-box?

---

### Post by rengglian on 2013-02-24
Thank you tgalati4, 
yep, next time I will post the output of /var/log/apt as well. 

Octave 3.2 worked out of the box, but it didn't produce "nice" plots IMO.

---

