---
title: "cabextract not configing"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by SolarKoka on 2008-10-29
> koka@koka-desktop:~$ cd cabextract-1.2
koka@koka-desktop:~/cabextract-1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


After I extracted the .tar.gz archive, I used the './configure' command in terminal, but for some reason it cannot configure it and gives out the above message.

[config.log]("http://www.mediafire.com/?iyxt1szn1kz")

---

### Post by Thelasko on 2008-10-29
That's not [how you install software in Ubuntu.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by dracayr on 2008-10-29
are you sure the package build-essential is installed? Make sure with ```
sudo apt-get install build-essential
```

dracayr

---

