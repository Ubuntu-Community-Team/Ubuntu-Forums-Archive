---
title: "I need to bootstrap my devlopment world..."
date: 2006-10-18
forum: Programming Talk
---

### Post by tananaBrian on 2006-10-18
Hi,

  I'm a noob, so be nice... 

  Just installed Ubuntu on a machine at home so I can learn Linux s/w development in c/c++, GTK+ etcetera.  I'm on dial-up ...26.4kbaud connection...

  I haven't tried to learn about apt-get or installing software packages from within Ubuntu yet because with my dial-up connection, it's pretty much a grand exercise in futility...

  I need, however, to get gcc and other related tools and libraries onto that machine.  My machine is an older Pentium III running dual-boot Windows XP Home and Ubuntu LTS v6.06.1.

  Is there any place online that I can d/l binaries for gcc to get me started?  I can d/l from at work and burn a CD or DVD, then carry it home ...and if I at least have gcc at home, then couldn't I then also build source code for the other packages?

  Please help me get started!

By,
Noob

---

### Post by po0f on 2006-10-18
tananaBrian,

[build-essential](http://packages.ubuntu.com/dapper/devel/build-essential) should be included on the installation CD.  If you want to do GTK development, install [libgtk2.0-dev](http://packages.ubuntu.com/dapper/libdevel/libgtk2.0-dev) and possibly [libgtkmm](http://packages.ubuntu.com/dapper/libdevel/libgtkmm-dev) for C++/GTK, though I'd probably recommend [wxGTK](http://packages.ubuntu.com/dapper/libdevel/libwxgtk2.6-dev) for C++ GUI stuff.

I don't know the exact directory to put debs for them to be recognized by Synaptic for installation, maybe start a new thread pertaining to that?

---

### Post by tananaBrian on 2006-10-19
Thanks for the pointers!  I've saved off everything and will go see what I can make of it.  Shall I assume that build-essential has gcc binaries in it?  I'll keep reading and looking and trying...

Thx,
Brian

---

### Post by po0f on 2006-10-19
tananaBrian,

Yes, build-essential includes gcc, g++, make, and libc6-dev, as well as dpkg-dev.  I wish these were installed by default, it took me a couple of hours after my first install before I found this package.

---

### Post by tananaBrian on 2006-10-19
Ok!  Thanks a mil!  Don't know why I didn't discover it before (I did endless web searches instead), but the 'Software Packages included in Dapper' web page that I found as a result of your hints has a lot more listed there as well.  Whew!  Feel soo much better ...now I can go get busy!

Brian

---

