---
title: "Configure cannot find KDE Ubuntu 12.04 ktechlab 0.3.7"
date: 2012-05-15
forum: Packaging and Compiling Programs
---

### Post by themrrobert on 2012-05-15
Trying to compile ktechlab 0.3.7 from source ( as the precompiled i386  .deb file won't install on 12.04)

[http://sourceforge.net/projects/ktechlab/files/ktechlab/0.3.7/](http://sourceforge.net/projects/ktechlab/files/ktechlab/0.3.7/)

Its the ktechlab-0.3.7 tar.bz2 file.

After installing all the other dependencies, when it gets to 
checking for KDE is replies with this:
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```

I've looked into the configure file to try and tell it where to find the kde libraries. 
 
Ubuntu 12.04 has removed the kdelibs4-dev package. It now uses kdelibs5-dev but it has the kde4 dev tools, just maybe named differently. I need to find out how to point it in the right direction.

If anyone could help I'd be immensely grateful

---

### Post by oldos2er on 2012-05-15
Moved to Packaging and Compiling Programs.

---

### Post by noodlebytes on 2012-07-23
The only "easy" solution I know so far is to install ktechlab first in Ubuntu 10.04 then directly upgrading to 12.04 via network upgrade. Upgrade must be done without removing the what-so-called "obsolete packages"... 

Or if you want, you can manually install each ktechlab dependencies. the list of dependencies are here: [http://packages.ubuntu.com/lucid/ktechlab]("http://packages.ubuntu.com/lucid/ktechlab") ...

By the way, I tried following the instructions in building ktechlab in 12.04 from [http://askubuntu.com/questions/116851/how-to-install-ktechlab]("http://askubuntu.com/questions/116851/how-to-install-ktechlab")
but then it fails somehow even if kde is already installed

---

