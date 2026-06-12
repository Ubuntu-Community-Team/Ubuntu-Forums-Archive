---
title: "gnome-system-tools Installation problems"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mrgooding on 2008-05-01
Hi All

i've had a quick search, but couldn't see any similar problems - i'm trying to install the gnome-system-tools 2.22.0 but get a problem when trying the configure part of the installation routine: here's what happens when I type ./configure (as specified in the installation instructions):

james@james-laptop:~/Documents/gnome-system-tools-2.22.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Am I doing something wrong, or do I perhaps need to install from somewhere else (i've tried from the desktop and my documents folder incase this was the problem).

Any help or pointers would be greatly appreciated - I can upload the config.log file if this is necessary.

Thanks!

---

### Post by Thingymebob on 2008-05-01
Why are you manually installing this, much better to use synaptic to do the job for you

---

### Post by mrgooding on 2008-05-01
I wasn't aware of that utility - i've just had a look and it says it's installed! thanks Thingymebob!

---

