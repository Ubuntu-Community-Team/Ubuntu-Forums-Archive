---
title: "problem with compiling"
date: 2008-05-03
forum: Packaging and Compiling Programs
---

### Post by aydinz on 2008-05-03
need help in compiling bluez-gnome-0.25 i type cd and the location then type ./configure and it comes up with an error as follows


aydin@aydin-desktop:~$ cd /home/aydin/Documents/bluezz/bluez-gnome-0.25
aydin@aydin-desktop:~/Documents/bluezz/bluez-gnome-0.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

can some1 help me out i just downloaded ubuntu a few days ago i got no idea whats going on...

---

### Post by jcwmoore on 2008-05-03
> **aydinz said:**
> need help in compiling bluez-gnome-0.25 i type cd and the location then type ./configure and it comes up with an error as follows


aydin@aydin-desktop:~$ cd /home/aydin/Documents/bluezz/bluez-gnome-0.25
aydin@aydin-desktop:~/Documents/bluezz/bluez-gnome-0.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

can some1 help me out i just downloaded ubuntu a few days ago i got no idea whats going on...

it looks like you are missing packages that are needed to compile from source, to get what you need run 
```
sudo apt-get build-dep *nameofprogramtocompile*
```

---

